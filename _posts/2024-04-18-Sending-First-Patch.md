## Sending First Patch

First we tried to make a basic patch correcting only the codestyle of some files, after which we did the following patch:

We have replaced bellow code in drivers/iio/adc/ad7266.c of Branch TESTING of repository IIO
```tsql
    ret = iio_device_claim_direct_mode(indio_dev);
    if (ret)
      return ret;
    ret = ad7266_read_single(st, val, chan->address);
    iio_device_release_direct_mode(indio_dev);
    
    val = (*val >> 2) & 0xfff;
    if (chan->scan_type.sign == 's')
    	*val = sign_extend32(*val,
    			     chan->scan_type.realbits - 1);
    
    return IIO_VAL_INT;
```
to
```
    iio_device_claim_direct_scoped(return -EBUSY, indio_dev)
      ret = ad7266_read_single(st, val, chan->address);
    
    *val = (*val >> 2) & 0xfff;
    if (chan->scan_type.sign == 's')
      *val = sign_extend32(*val,
           chan->scan_type.realbits - 1);
    
    return IIO_VAL_INT;
    unreachable();
```
Which will make error handling more natural and possibly simplify code.

These patchs have to be sending to the teacher and monitor of the course to check if everything is in accord of recommendation and if it works on Kernel.

When my duo tried to send the codestyle patch, an error appeared regarding the e-mail, and then he gave up on sending the patch.

And I have a lot of trouble trying to sending this patch too, such as I haven't installed the git send-email command, I need also configure my SMTP, also doing a lot of changes in the commit file to write it in the correctly form. But after all everything is ok and the patch was sending to the monitor. Hope we get the feedback soon!
