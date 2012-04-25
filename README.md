I used the following [instructions](http://code.google.com/p/wkhtmltopdf/wiki/compilation) from [Nicholas](http://code.google.com/u/103497416405410181471/) to compile wkhtmltopdf & wkhtmltoimage

> For those installing on Mac OS X 10.6.8, these are the steps I followed to get a successful build:
> 
> $ git clone git://gitorious.org/+wkhtml2pdf/qt/wkhtmltopdf-qt.git
> $ cd wkhtmltopdf-qt
> $ git checkout staging
> 
> Perform a find/replace across all files in the 'wkhtmltopdf-qt' folder (I did this using BBEdit):
>    FIND:    MACOSX_DEPLOYMENT_TARGET = 10.4
>    REPLACE: MACOSX_DEPLOYMENT_TARGET = 10.6
>
> $ QTDIR=. ./bin/syncqt
> 
> $ ./configure -sdk /Developer/SDKs/MacOSX10.6.sdk -arch x86 -release -static -fast -exceptions -no-accessibility -no-stl -no-sql-ibase -no-sql-mysql -no-sql-odbc -no-sql-psql -no-sql-sqlite -no-sql-sqlite2 -no-qt3support -xmlpatterns -no-phonon -no-phonon-backend -webkit -no-scripttools -no-mmx -no-3dnow -no-sse -no-sse2 -no-ssse3 -qt-zlib -qt-libtiff -qt-libpng -qt-libmng -qt-libjpeg -openssl -graphicssystem raster -opensource -nomake "tools examples demos docs translations" -no-opengl -no-dbus -no-framework -no-dwarf2 -no-multimedia -no-declarative -largefile -rpath -no-nis -no-cups -no-iconv -no-pch -no-gtkstyle -no-nas-sound -no-sm -no-xshape -no-xinerama -no-xfixes -no-xrandr -no-xrender -no-mitshm -no-xkb -no-glib -no-openvg -no-xsync -no-javascript-jit -no-egl -carbon --prefix=../wkqt/
> $ make -j3 
> $ make install
> $ cd ..
> 
> $ wget http://wkhtmltopdf.googlecode.com/files/wkhtmltopdf-0.11.0_rc1.tar.bz2
> $ tar -xvf wkhtmltopdf-0.11.0_rc1.tar.bz2
> $ cd wkhtmltopdf-0.11.0_rc1
> 
> $ ../wkqt/bin/qmake
> $ make
> $ sudo make install


**Compile Notes**

when running ../wkqt/bin/qmake, I received the following error

````wkqt qmake malloc: *** error for object 0xbfffce20: pointer being freed was not allocated

on the subsequent 'make' command, hundreds of warnings were printed in reference to qmake files not being visible. I'd copy the warnings verbatim, but they're gone now.


**Tests**

````
$ wkhtmltoimage news.ycombinator.com hacker_news.jpg
Loading page (1/2)
Rendering (2/2)
Done
````

````
$ wkhtmltopdf news.ycombinator.com hacker_news.pdf
Loading pages (1/6)
Counting pages (2/6)
Resolving links (4/6)
Loading headers and footers (5/6)
Printing pages (6/6)
Done
````
