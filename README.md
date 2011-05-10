HTML5 AJAX File Uploader
==============================

**This file provides a JavaScript object to simplify utilization of the HTML5 File API for AJAX uploading.**

The only thing you need to do is include the uploader.js file and create the object with

	var upload = new uploader(document.getElementById('file-input-element'), {options});

You don't have to create a new object for each input element if you don't want to. I made it so the setOpt() and setInput() methods chain together so you can just change what's necessary without instantiating unnecessary uploader objects (and thus XmlHttpRequest objects)

## Options

* prefix:string - this string is the name that files will be sent to the server as, i.e. files[0] will be sent as prefix+'0' and files[1] will be sent as prefix+'1', etc.
* multiple:boolean - set to *true* if you want to allow multiple files to be uploaded at once, *false* to only upload the first file (and only file if the multiple attribute isn't specified on the input element)
* autoUpload:boolean - set to *true* so that the files are uploaded as soon as they are selected, *false* to manually send
* url:string - the URL to which the data will be sent
* onprogress:function - callback function for whenever the progress event fires (so you can update a progress bar or whatever)
* error:function - callback function for whenever the upload errors out
* success:function - callback function for when the AJAX request completes, i.e. the XHR status == 200

## Methods

* send() - attempt to send whatever files are currently selected in the input element
* setOpt() - set one of the options after instantiation
* getOpt() - returns one of the options
* setInput() - set the object to a new input element
* getInput() - returns the input element

## To Do List

This seems pretty complete to me since I explicitly wanted to make this thing pretty barebones. The less I had built into the object, the more I could easily customize things as I needed when using the object.

* Automatically detect the *multiple* attribute on the element? It doesn't seem to make much difference to me, but then again, it also doesn't seem plausible that someone would declare the *multiple* attribute but only allow uploading of one file at a time
* Possibly attempt to utilize only one XHR object even if multiple uploader objects are created, but who knows
* Grab the input element for the user if a string is passed instead of the DOM input element object