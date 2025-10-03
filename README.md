# Coding Assignment 4: Medical Image Segmentation with U-Net

In previous assignments, you built CNNs for classification. Now, we will dive into a more complex and impactful computer vision task: **semantic segmentation**. You will build, train, and evaluate a U-Net, a state-of-the-art deep learning architecture, to segment brain tumors from multi-modal MRI scans.

This two-part assignment will guide you through the complete workflow of a medical imaging project, from exploring a complex dataset to building and experimenting with a powerful segmentation model. By the end, you will have hands-on experience with one of the most prominent applications of CNNs in the medical field.

## About the Dataset: BraTS 2020

We will be using the **[BraTS 2020 (Brain Tumor Segmentation) dataset](https://www.kaggle.com/datasets/awsaf49/brats20-dataset-training-validation)**, a challenging and widely-used benchmark in the medical imaging community. Each patient case includes four co-registered MRI modalities:
* T1-weighted (T1)
* Post-contrast T1-weighted (T1ce)
* T2-weighted (T2)
* T2-weighted FLAIR (Fluid-Attenuated Inversion Recovery)

Your goal will be to use these scans to predict the location and extent of gliomas, segmenting regions such as the necrotic core, edema, and the enhancing tumor.

## Learning Objectives

After completing this assignment, you will be able to:

* **Implement a U-Net architecture** from scratch in PyTorch for semantic segmentation.
* **Understand and preprocess multi-modal medical imaging data** (NIfTI format, MRI sequences).
* **Evaluate segmentation models** using domain-specific metrics like the Dice coefficient and Jaccard Index (IoU).
* **Experiment with different loss functions**, modalities, and data sampling strategies to improve model performance.
* **Transition a model from a binary to a multi-class segmentation task**, a key step in building more sophisticated models.

</br>

## Assignment Structure

This assignment is broken down into two notebooks that represent a complete project workflow.

1.  **`CA4.1_BraTS2020_EDA.ipynb`**
    
    This notebook is a guided tutorial on Exploratory Data Analysis (EDA) for the BraTS 2020 dataset. It contains **13 questions**. For the first 11 questions, you are only required to run the provided code cells and answer based on your observations and interpretations. No coding is needed. Some questions are domain-specific; focus on careful observation rather than searching for a single "correct" answer. Only the final two questions will require you to run and modify a code cell to generate visualizations for your answer.

2.  **`CA4.2_BrainTumorSegmentation.ipynb`**
    
    Here, you will build and train a U-Net model. The notebook culminates in **7 experimental questions** at the end. These are hands-on tasks where you will modify the baseline model to explore different techniques. Each question includes code skeletons with `TODO` sections for you to complete, along with helpful hints.

</br>

---

### Setup and Environment on Explorer HPC

This assignment **must be completed on the Explorer HPC**, as the dataset is large and has been pre-loaded for your convenience. The notebook paths are already configured to read from the correct location on the HPC filesystem.

The easiest way to use the HPC is through the [Open OnDemand (OOD) web interface](https://ood.explorer.northeastern.edu/). A Python environment with all necessary packages (`pyTorch`, `nibabel`, etc.) has been created for you at: `/courses/CS7150.202610/shared/venvs/pyT`

There are two ways to use this environment for your Jupyter session:


#### **Method A: Pointing Directly to the Python Executable**
This is the simplest method and does not require any command-line work.

1.  Log in to [Open OnDemand (OOD)](https://ood.explorer.northeastern.edu/).
2.  Navigate to `Interactive Apps > JupyterLab Notebook`.
3.  Fill out the session request form.
4.  Check the box that says **"Local Anaconda install instead of one of the Anaconda modules"**.
5.  A text field labeled **"Path to Custom Anaconda Install"** will appear. Paste the following path into it:
    ```
    /courses/CS7150.202610/shared/venvs/pyT/bin
    ```
6.  Launch the session. Your JupyterLab environment should automatically use the correct Python environment and all pre-installed packages.


#### **Method B: Installing the Environment as a Jupyter Kernel (Easier, one-time setup)**
If Method A gives you trouble, or if you prefer to have the environment appear as a named kernel in your Jupyter launcher, you can perform this one-time setup.


1.  Log in to [Open OnDemand (OOD)](https://ood.explorer.northeastern.edu/).
2.  Start a terminal session by going to `Clusters > Explorer Shell Access`.
3.  Once the terminal is running, run the following two commands in order: 

    Get on a compute node
    ```bash
    srun -p courses --pty bash
    ```
    
    Activate the shared Python environment
    ```bash
    source activate /courses/CS7150.202610/shared/venvs/pyT
    ```

    Install this environment as a personal Jupyter kernel
    ```bash
    python -m ipykernel install --user --name pyT --display-name "Python (pyTorchEnv)"
    ```

    Get off the compute node
    ```bash
    exit
    ```

4.  After this is done, you can stop the terminal session. From now on, when you start a regular JupyterLab Notebook session on OOD, you will see **"Python (pyTorchEnv)"** in the list of available kernels to select.

</br>

**Helpful Links:**
* **Getting started with Explorer:** Refer to this [document](https://docs.google.com/document/d/1nsP4YUBajdM6j3R0tA4gRnwo9qPdRv5gTtXHYdiXCz8/) to create environments, manage files, and start sessions in our HPC. 
* **Official Documentaion:** For more info on the HPC, refer to the [Official Documentation](https://rc-docs.northeastern.edu/en/latest/).

---
### Submission Instructions

1.  Complete all tasks for both notebooks:
    * In `CA4.1`, answer all 13 in-line questions.
    * In `CA4.2`, complete all `TODO` sections and answer the 7 experimental questions at the end.

2.  Zip both completed notebooks (`.ipynb` files) into a single file. You may also include a PDF if you chose to report in one. Name the zip file `CA4-Your-Last-Name`.

3.  Submit the zip file as a direct **reply** to the [*coding assignment module of week 5*](https://northeastern.instructure.com/courses/226141/discussion_topics/2877268?module_item_id=12458398) on Canvas.

### Getting Help

If you encounter any problems with the notebook, notice any errors, or have questions about the setup, please do not hesitate to reach out. You can email me at **[patel.pranav2@northeastern.edu](mailto:patel.pranav2@northeastern.edu)** or send me a message on Microsoft Teams.

### Important Notes

* Please adhere to the collaboration policy outlined in the course syllabus.
* Make sure to credit any external resources, discussions, or AI assistance you used to complete the assignment.
* **Start early!** This is a comprehensive assignment that will translate much of our theoretical knowledge into practical application. Good luck!