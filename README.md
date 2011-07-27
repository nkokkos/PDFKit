# Forked version for windows xp systems

I wanted to generate a pdf from my windows xp system since I was developing on that box. 
Make sure that you have installed wkhtmltopdf for windows from
h**p://code.google.com/p/wkhtmltopdf/downloads/detail?name=wkhtmltopdf-0.9.9-installer.exe&can=2&q=

Look at the commit history for the changes I made to this forked version. 
 

# PDFKit

Create PDFs using plain old HTML+CSS. Uses [wkhtmltopdf](http://github.com/antialize/wkhtmltopdf) on the backend which renders HTML using Webkit.

## Installation

1. Install wkhtmltopdf (optional)
** PDFKit comes bundled with wkhtmltopdf binaries for Linux i386 and OS X i386
** PDFKit defaults to user installed versions of wkhtmltopdf if found
** Installing wkhtmltopdf binary
*** Download the latest binary from http://code.google.com/p/wkhtmltopdf/downloads/list
*** Place the binary somewhere on your path (e.g /usr/local/bin)
2. Install PDFKit

    $ gem install pdfkit
   
## Usage
    
    # PDFKit.new takes the HTML and any options for wkhtmltopdf
    # run `wkhtmltopdf --extended-help` for a full list of options
    kit = PDFKit.new(html, :page_size => 'Letter')
    kit.stylesheets << '/path/to/css/file'
    
    # Git an inline PDF
    pdf = kit.to_pdf
    
    # Save the PDF to a file
    file = kit.to_file('/path/to/save/pdf')
    
    # PDFKit.new can optionally accept a URL or a File.
    # Stylesheets can not be added when source is provided as a URL of File.
    kit = PDFKit.new('http://google.com')
    kit = PDFKit.new(File.new('/path/to/html'))
   
## Middleware

PDFKit comes with a middleware that allows users to get a PDF view of any page on your site by appending .pdf to the URL.

### Middleware Setup

**Non-Rails Rack apps**
   
    # in config.ru
    require 'pdfkit'
    use PDFKit::Middleware
    
**Rails apps**

    # in application.rb(Rails3) or environment.rb(Rails2)
    require 'pdfkit'
    config.middleware.use PDFKit::Middleware
    
**With PDFKit options**

    # options will be passed to PDFKit.new
    config.middleware.use PDFKit::Middleware, :print_media_type => true


## Note on Patches/Pull Requests
 
* Fork the project.
* Make your feature addition or bug fix.
* Add tests for it. This is important so I don't break it in a
  future version unintentionally.
* Commit, do not mess with rakefile, version, or history.
  (if you want to have your own version, that is fine but bump version in a commit by itself I can ignore when I pull)
* Send me a pull request. Bonus points for topic branches.

## Copyright

Copyright (c) 2010 Jared Pace. See LICENSE for details.
