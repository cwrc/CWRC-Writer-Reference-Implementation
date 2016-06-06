# CWRC-Writer-Reference-Implementation

CWRC-Writer (https://github.com/cwrc/CWRC-Writer) is a a JQuery customization of the TinyMCE editor for in-browser XML editing and stand-off RDF annotation.

![Alt Text](https://raw.githubusercontent.com/cwrc/CWRC-Writer-Reference-Implementation/master/docs/images/editor.png)

The CWRC-Writer is meant to be embedded within other pages, interacting with outside services including:

 - a document store
 - an annotation store
 - an XML validation service
 - an entity lookup and authoring service
 - an XML schema or schemas
 - and XML template store

The CWRC-Writer has been designed to interact with these services through one of two APIs:

- client-side, in the browser javascript as a 'delegator'
- server-side, as a RESTful API  

Herein we define both APIs and provide a reference implementation for both APIs.  The reference implementation is intended for evaluation of the CWRC-Writer and not for production use.

In a separate project we provide alternate 'delegators' and associated server-side API stubs, that can be used to ease the work of linking the CWRC-Writer to other backend providers.

