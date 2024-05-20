## First Contribution in open source software

After correcting the errors handled by the monitor, I sent the new patch to the IIO maintainers, the message is as follows:
```
Switching to the _scoped() version can make the error
handling more natural instead of delayed until direct
mode was released.

Co-developed-by: Eduardo Figueredo <eduardofp@usp.br>
Signed-off-by: Eduardo Figueredo <eduardofp@usp.br>
Signed-off-by: Fernando Yang <hagisf@usp.br>
---
 drivers/iio/adc/ad7266.c | 15 +++++++++------
 1 file changed, 9 insertions(+), 6 deletions(-)

diff --git a/drivers/iio/adc/ad7266.c b/drivers/iio/adc/ad7266.c
index 8b03d4469..3fc34a3a8 100644
--- a/drivers/iio/adc/ad7266.c
+++ b/drivers/iio/adc/ad7266.c
@@ -63,12 +63,14 @@ static int ad7266_powerdown(struct ad7266_state *st)
 static int ad7266_preenable(struct iio_dev *indio_dev)
 {
        struct ad7266_state *st = iio_priv(indio_dev);
+
        return ad7266_wakeup(st);
 }

 static int ad7266_postdisable(struct iio_dev *indio_dev)
 {
        struct ad7266_state *st = iio_priv(indio_dev);
+
        return ad7266_powerdown(st);
 }

@@ -151,15 +153,16 @@ static int ad7266_read_raw(struct iio_dev *indio_dev,

        switch (m) {
        case IIO_CHAN_INFO_RAW:
-               iio_device_claim_direct_scoped(return -EBUSY, indio_dev)
+               iio_device_claim_direct_scoped(return -EBUSY, indio_dev) {
                        ret = ad7266_read_single(st, val, chan->address);

-               *val = (*val >> 2) & 0xfff;
-               if (chan->scan_type.sign == 's')
-                       *val = sign_extend32(*val,
-                                                chan->scan_type.realbits - 1);
+                       *val = (*val >> 2) & 0xfff;
+                       if (chan->scan_type.sign == 's')
+                               *val = sign_extend32(*val,
+                                                        chan->scan_type.realbits - 1);

-               return IIO_VAL_INT;
+                       return IIO_VAL_INT;
+               }
                unreachable();
        case IIO_CHAN_INFO_SCALE:
                scale_mv = st->vref_mv;
-- 
2.34.1
```
Also, I sent a PR to the kw project correcting some code style errors:

```
- distro=$(cat /etc/*-release | grep -w 'ID\(_LIKE\)\?' | cut -d = -f 2 | xargs echo)
+ distro=$(grep < /etc/*-release --word-regexp 'ID\(_LIKE\)\?' | cut --delimiter = --fields 2 | xargs printf)
```

But due to the [SC2294](https://www.shellcheck.net/wiki/SC2294) shellcheck error, I'm not able to commit the code and need to fix this problem first.

First I tried to remove the eval:
```
-  eval "$@"
+  "$@"
```
But it didn't pass the unit test (And I only noticed it whe I'm sending the PR 🤦‍♂️), so I had to take another solution by replace the @ to *:
```
- eval "$@"
+ eval "$*"
```
Finaly, with some help of monitor about git rebase, it finaly works and the PR was updated correctly for project of kw.
