## Debian Packaging Final Steps

I asked our lecturer, Joenio Marques, about the possible causes of the errors reported in the previous post. He replied that the first one could be caused by the fact that there are temporary files inside the folder that caused a local change at the time of the build, or maybe it's the reason for the related global variables such as $PERL5_LIB or $PERL5_PATH.

After deleting all the related global variables and repackaging, the problem was solved, and furthermore, when I went to run the second error from yesterday, it also mysteriously disappeared. 

Now I've fixed all the errors, I've already reported the ITP too, all that's left is for the Salsa team to accept my request to upload the package.
