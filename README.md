# webserv
      (c) 2000, 2001, 2002, 2003 Cal Dixon
      Requires Rebol/Core 2.5 or Rebol/View 1.0 or later
         By default the server will look for pages to serve in a folder called "www" in the
      current directory.  It will listen on port 80 and generate a log-file called
      "webserv.log".  Files with unrecognized types will be sent as "text/html".
      Settings can be changed by creating a configuration file called "webserv-cfg.r".
      EXAMPLE configuration file ---- cut here ---
         wwwpath: %www/path        ; change this to where the files are...
         port: 8080                ; change this to whatever port the server should listen to
         logfile: %webserv.log     ; the name of the logfile or set to none
         default-type: "application/octet-stream" ; Content-Type for unrecognized extensions
      --- cut here --- END of example file
      To make the server recognize additional content types, create a file called
      "content-types.r" and list pairs of extensions (without the dot) and content types.
      EXAMPLE content-type file ---- cut here ---
      "lha" "application/octet-stream"
      "png" "image/png"
      "mp3" "audio/mp3"
      "rar" "application/x-rar-compressed"
      "rtf" "application/rtf"
      "zip" "application/x-zip-compressed"
      --- cut here --- END of example file

      Files with an extension of ".r" or ".cgi" or in a folder called "cgi-bin/" will be treated
      as Rebol CGI scripts.  Output from CGI scripts was not buffered in versions before 0.0.0.12,
      but now is buffered before sending anything.
      Files with an extension of ".rhtml" are pre-proccesed by the server.  Anything enclosed
      in a pair of ":[" and "]:" will be executed as rebol code and the value of the expression
      will be inserted into the document at that location.

      To start the server:
         Place the %webserv.r script in a folder, start up rebol, change to the directory
         the script is in, then type "do %webserv.r".}
