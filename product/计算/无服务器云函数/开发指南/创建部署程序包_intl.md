A deployment package is a zip collection of all the code and dependencies that SCF runs, which should be specified during function creation. You can create a deployment package in your local environment and upload it to SCF, or write the code directly in the SCF console. This will create and upload the deployment package for you. Use the following criteria to determine if you can use the console to create a deployment package:

- Simple scenario: If your custom code only needs to use standard libraries or SDK libraries such as COS and SCF libraries provided by Tencent Cloud, and there is only one code file, you can use the online editor in the SCF console. The console automatically compresses the code and associated configuration information into a runnable deployment package.
- Advanced scenario: If your code requires additional resources (such as a graphics library for image processing, web framework for web programming, or database connection library for executing database commands), you need to first create a function deployment package in your local environment and then upload it to the console.

## Packaging Requirements

### ZIP Format

The code package submitted directly to the SCF platform or submitted by uploading to COS and then importing into SCF must be in [ZIP format](https://zh.wikipedia.org/zh-hans/ZIP%E6%A0%BC%E5% BC%8F). 7-Zip can be used on Windows and ZIP command can be used on Linux for compression or decompression.

### Packaging Method

When packaging, you need to package the code files but not the entire directory of the code; after packaging is completed, the entry function file needs to be in the root directory of the package.

When packaging on Windows, you can enter the function code directory, select all files, right-click and select "Send to > Compressed (zipped) folder" to create the deployment package. After the zip package is unzipped with a tool such as 7-Zip for file browsing, the entry function and other libraries should be present.

When packaging on Linux, you can enter the function code directory, call the zip command, and specify the source files as all files in the code directory to generate the deployment package, such as `zip /hoem/scf_code.zip * -r`.

## Sample Deployment Package

The following sample illustrates the steps for creating a deployment package in a local environment.


>**Notes:**
>1. Usually, locally installed dependent libraries also work well on the SCF platform, but in certain cases, the binary files installed may cause compatibility problems. If this occurs, please [contact us](https://cloud.tencent.com/document/product/583/9712).
>2. For the Python programming language in the sample, libraries and dependencies will be installed locally using the pip tool. Please make sure that you have Python and pip installed locally.



### Python Deployment Package

#### Creating a Python deployment package in Linux

1) Create a directory:

```
mkdir /data/my-first-scf
```

2) Save all the Python source files (.py files) of the function created into this directory. For more information about how to create a function, see [Getting Started - Creating a DownloadImage Function](https://cloud.tencent.com/document/product/583/9211).

3) Install all dependencies to this directory using pip:

```
pip install <module-name> -t /data/my-first-scf
```

For example, the following command installs the Pillow library in the my-first-scf directory:

```
pip install Pillow -t /data/my-first-scf
```

4) Compress everything in the my-first-scf directory. Please note that you need to compress the content of the directory instead of the directory itself:

```
cd /data/my-first-scf && zip my_first_scf.zip * -r
```


>**Notes:**
>1. For libraries with compilation process, in order to maintain the consistency with the SCF runtime environment, it is recommended to perform the packaging under CentOS 7.
>2. If there are other software, compilation environment, or development library requirements during the installation or compilation process, please solve the compilation and installation problems as instructed.


#### Creating a Python deployment package in Windows

It is recommended that you package the dependent package and code that have been successfully executed in Linux into a zip package as the execution code of the function. For details, see [Code Practices - Obtaining Images in COS and Creating Thumbnails](https://cloud.tencent.com/document/product/583/9736).

In Windows, you can also use the `pip install <module-name> -t <code-store-path>` command to install the Python libraries, but for packages that need to be compiled or have static or dynamic libraries, libraries generated by compiling in Windows cannot be called in the SCF runtime environment (CentOS 7), so library installation in Windows is only suitable for pure Python implementations.


