## Introduction


Data frames are one of the essential parts of the data science toolkit. They are the specialized data structures for tabular data sets that provide us with a simple and powerful API for summarizing, cleaning, and manipulating a wealth of data sources that are currently cumbersome to use.

A data frame is like a database inside a variable. It is an object which can be created, modified, copied, serialized, debugged, inspected, and garbage collected. It allows you to communicate with your data quickly and effortlessly, using just a few lines of code. The DataFrame project is similar to the _pandas_library in Python or the built-in _data.frame_class in R.

This booklet serves as the main source of documentation for the DataFrame project in Pharo. We'll start by describing the complete API of the DataFrame and DataSeries data structures, providing examples for each method. Then we'll show how data frames can be used in practice in a series of hands-on tutorials.

### The DataFrame project


DataFrame v1.0 was the first implementation of data frames in Pharo. It was created by Oleksandr Zaitsev in 2017 as a Google Summer of Code project and was presented at the 25th International Smalltalk Joint Conference \(ESUG 2017\) in Maribor, Slovenia.

Thanks to the questions, requests, and suggestions of numerous people who were using DataFrame, the API was improved, some major bugs were fixed, several methods were aggressively optimized, and new features were added. Now with this booklet, we are happy to present the cleaned, improved, and updated DataFrame v2.0.

### Who is this booklet for?


DataFrame was designed for anyone working with tabular data in Pharo. Being designed by a data scientist, the emphasis is on the typical data analysis that is commonly performed in a data science or machine learning workflow. However, knowledge of machine learning or statistics is not required to read this booklet or work with DataFrame.

On the other hand, familiarity with the Pharo programming language and environment is a prerequisite. In the next section, we'll briefly introduce Pharo. But it is also strongly recommended to learn Pharo and make sure that you are comfortable with it before you proceed to the following chapters.

DataFrame was designed in the tradition of Smalltalk and with _smalltalkers_ in mind. If you come from a Python, R, or SQL background, some elements of the API might seem strange to you. But stick around and you will come to love the Smalltalk ways.

### What is Pharo?


Pharo is a dynamic, purely object-oriented programming language \(everything is an object\) in the tradition of Smalltalk. But it is also a powerful development environment, focused on simplicity and immediate feedback. Its entire syntax fits on a postcard, and coding can be done directly in the debugger. Pharo has super cool tools that empower you and make you highly efficient.

Pharo's goal is to deliver a clean, innovative, free and open-source immersive environment. By providing a stable and small core system, excellent development tools, and maintained releases, Pharo is an attractive platform to build and deploy mission-critical applications.

Pharo fosters a healthy ecosystem developed by both private and commercial contributors who advance and maintain the core system and its external packages. More information about Pharo is available at http://www.pharo.org/. If you are new to Pharo, we suggest you take the Pharo MOOCor read the Pharo by Examplebook.

DataFrame v2.0 was tested on stable versions of Pharo 6.1 and Pharo 7.0, as well as on the development version of Pharo 8. Through continuous integration \(CI\) and 90% code coverage by unit tests, we try to make sure that DataFrame is working well on every latest stable and development version of Pharo on all major operating systems: Linux, Mac OS, and Windows, as well as both 32-bit and 64-bit architectures.

So before moving on to the next chapter, go to [https://pharo.org/download](https://pharo.org/download) and get yourself the latest Pharo. We strongly suggest that you try out all the examples as you read this booklet. It will help you understand what data frames are and how they can be used.

### The PolyMath project


DataFrame was originally created as part of the PolyMath project - an open-source initiative that brings the power of scientific computing to Pharo. It started with the creation of the _PolyMath_library - a general purpose numerical computation framework in Pharo, similar to the _numpy_and _scipy_libraries in Python, as well as the _SciRuby_library and the built-in functionality of R and Julia.

PolyMath provides two main data structures: `PMMatrix` and `PMVector`, and covers topics such as statistical moments, polynomials, interpolations, integration, series \(not to be confused with the data series that will be discussed in the following chapters\), vector algebra, ordinary differential equations, complex numbers, quaternions, KD-trees, random number generation, arbitrary floating-point arithmetics, etc.

The original version of PolyMath was described in the book _Numerical methods in Smalltalk_ by Didier Besset. Since then, PolyMath has changed a lot, and now, thanks to many different contributors, it has grown into a fully functional framework for numerical computations.

Besides PolyMath itself, the PolyMath organization on GitHub hosts other projects, including DataFrame, described in this booklet, and _libtensorflow-pharo-bindings_-- a Pharo bridge to Google's _TensorFlow_library.

### Terminology


At this point, you have probably noticed that, depending on the context, the phrase "data frame" can refer to several different things. It can be a data structure, a class, a package, or this whole project. To remove these ambiguities from our language, we propose the following terminology and stick to it in this booklet:



data frame
-- a general reference to the tabular data structure \(collection\) designed for data analysis.

data series
-- a general reference to a dictionary-like data structure that is used to represent rows and columns of a data frame.

DataFrame
-- the class name of a data structure that models a data frame, or a reference to the DataFrame package or project.

DataSeries
-- the class name of a data structure used to model a data series.

We would also like to remind you that _"series"_ is both a singular and a plural form. We say _"a single data series was created"_ and _"two data series were removed"_.

### Structure of this booklet


The rest of this booklet is structured in the following way:

- **Chapter 1. DataFrame by example** - this chapter will guide you through the complete API of the DataFrame project using simple examples.
- **Chapter 2. Tutorials** - a series of short tutorials that will teach you to work with data frames and demonstrate how they can be applied to practical problems.


### How to contribute?


DataFrame is an open-source project released under the MIT public license. Although the original codebase was written by Oleksandr Zaitsev, the DataFrame project is the collaborative effort of many people who helped by giving advice, sharing ideas, reporting issues, and suggesting how to resolve them. There are many ways in which you can help make DataFrame better.

If you want to implement new features or improve existing functionality, you can fork the DataFrame repository on GitHub, make your changes, and create a pull request.

But contributions can be more simple and less time consuming. You can report a bug, suggest a better API, or request new features for DataFrame. All that can be done by creating dedicated issues in DataFrame's repository on GitHub.

Positive feedback is also very important. It is always very encouraging to hear how people use your project. So if you want to share your experience working or just playing with DataFrame, you can write about it on social media using the `#Pharo` and `#PharoDataFrame` hashtags. Also, feel free to contact me by email at _olk.zaytsev@gmail.com_.
