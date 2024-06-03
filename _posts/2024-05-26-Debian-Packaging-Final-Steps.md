## Debian Packaging Final Steps

I asked our lecturer, Joenio Marques, about the possible causes of the errors reported in the previous post. He replied that the first one could be caused by the fact that there are temporary files inside the folder that caused a local change at the time of the build, or maybe it's the reason for the related global variables such as $PERL5_LIB or $PERL5_PATH.

After deleting all the related global variables and repackaging, the problem was solved, and furthermore, when I went to run the second error from yesterday, it also mysteriously disappeared. 

Now I've fixed all the errors, I've already reported the ITP too, all that's left is for the Salsa team to accept my request to upload the package.

In addition, in class on Thursday, the teacher told us what we should do in the next stages, which in this case would be to choose a project and contribute to it.

I discussed it with my partner and we decided that we would follow the kworflow contribution flow, but since there was an [feedback requesting change](https://lore.kernel.org/linux-iio/20240508155435.183850-1-hagisf@usp.br/) in the first patch we sent to the kernel, we divided the tasks.

I'm going to fix the errors in the patch because I made the patch and I'm more familiar with it, while he made the start of the kw.

I hope it all works out.
