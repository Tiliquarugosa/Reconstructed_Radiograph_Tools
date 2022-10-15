# Reconstructed_Radiograph_Tools
 
Hello and welcome to my honours project for Curtin University Bachelor of Radiation Science (Medical Imaging).

This repository contains a set of tools for manipulating CT data with Python. It was written in Jupyter Notebook using Anaconda Navigator to manage dependencies.


#### perspectiveless_DRR.ipynb ####
This Notebook can import a DICOM directory as a 3D numpy array, and then creates an average intensity projection over the entire dataset. The result closely resembles an x-ray but does not account for geometric factors such as beam divergence or source image distance. The Notebook contains some examples where the performance of this algorithm is timed, and some examples to demonstrate the same process in the sagittal and coronal plane.


#### projection_library.py and projection_example.ipynb ####
These are a set of tools that let you create a simple DRR with perspective. It will let you import a DICOM directory, set geometric factors, and also save as a DICOM file. The DICOM saving function, save_dicom() is barebones. It saves to the same directory as the algorithm itself. It uses a default file from PyDicom and changes the image attributes. This means that the header information is not correct, but there is no way of transfering the patient information to the generated image by accident. The DICOM file will likely need windowing to look as expected once opened with any DICOM reading software.

projection_example is a Notebook that has the whole process working. projection_library is the functions alone, intended to be easy to import into other projects. Please note that you will want to run small-scale dummy data (eg. np.ones((3,3,3)) ) through both project() and add_img() to gain the benefit of Numba acceleration. Without acceleration, both functions will run very slowly.
