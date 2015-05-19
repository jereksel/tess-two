# tess-two

A fork of Tesseract Tools for Android ([tesseract-android-tools][tesseract-android-tools]) that adds some 
additional functions. Tesseract Tools for Android is a set of Android APIs and
build files for the [Tesseract OCR][tesseract-ocr] and [Leptonica][leptonica] image processing libraries.

This project works with Tesseract pre-release v3.04 and Leptonica v1.72. The required source code for Tesseract and
Leptonica is included within the `tess-two/jni` folder.

The `tess-two` subdirectory contains tools for compiling the Tesseract and Leptonica
libraries for use on the Android platform. It contains an Android [library project][library-project] 
that provides a Java API for accessing natively-compiled Tesseract and Leptonica APIs.

The `eyes-two` subdirectory contains a second, separate library project with additional image 
processing code copied from the [eyes-free project][eyes-free]. It includes native functions for text detection, blur detection, optical flow 
detection, and thresholding. Building eyes-two is not necessary for using the Tesseract or Leptonica APIs.

The `tess-two-test` subdirectory contains Android JUnit tests.

## Requirements

* Android 2.2 or higher
* A v3.02 [trained data file][tessdata] for a language. Data files must be extracted to a subdirectory named `tessdata`.

## Versions

Release points are tagged with [version numbers][semantic-versioning]. A change to the major version number
indicates an API change making that version incompatible with previous versions.

## Building

This project is set up to build on Android SDK Tools r22.3+ and Android NDK r10d+. The build
works on Linux, Mac OS X, and Windows 7/8. See [Issues][issues] for reported build issues.

On 64-bit Ubuntu, you may need to install the `ia32-libs` 32-bit compatibility library.

To build the latest tess-two code, run the following commands in the terminal:

    git clone git://github.com/rmtheis/tess-two tess
    cd tess
    cd tess-two
    ndk-build
    android update project --path .
    ant release

To build eyes-two, additionally run the following:

    cd ..
    cd eyes-two
    ndk-build
    android update project --path .
    ant release

After building, the tess-two and eyes-two projects can be imported into Eclipse using 
File->Import->Existing Projects into Workspace.

## Maven

While this project does not require Maven (and this project has not yet been registered in a 
Maven central repository), it can be [integrated into a local Maven repository for convenience][maven].

## Questions

If you have a question, consider posting it to [StackOverflow][stackoverflow] and tagging it with the 
`tess-two` tag. For best results, follow their suggestions for [asking a good question][how-to-ask].

## Contributing

Pull requests are always welcome. Please open a new issue if you find a bug.

## License

    Copyright 2011 Robert Theis
    
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at
    
        http://www.apache.org/licenses/LICENSE-2.0
    
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


[tesseract-android-tools]: https://code.google.com/p/tesseract-android-tools/
[tesseract-ocr]: https://github.com/tesseract-ocr/tesseract
[leptonica]: http://www.leptonica.com/
[library-project]: https://developer.android.com/tools/projects/projects-eclipse.html#ReferencingLibraryProject
[eyes-free]: https://code.google.com/p/eyes-free/
[tessdata]: https://github.com/tesseract-ocr/tessdata
[semantic-versioning]: http://semver.org
[issues]: https://github.com/rmtheis/tess-two/issues
[maven]: http://www.jameselsey.co.uk/blogs/techblog/tesseract-ocr-on-android-is-easier-if-you-maven-ise-it-works-on-windows-too/
[stackoverflow]: https://stackoverflow.com/
[how-to-ask]: https://stackoverflow.com/help/how-to-ask
