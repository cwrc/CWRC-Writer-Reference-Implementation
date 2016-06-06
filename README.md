# CWRC-Writer-Reference-Implementation

CWRC-Writer (https://github.com/cwrc/CWRC-Writer) is a a JQuery customization of the TinyMCE editor for in-browser XML editing and stand-off RDF annotation.  The CWRC-Writer provides standard XML WYSIWYG editing, enhanced with an intuitive XML structure view, enhanced tagging, and support for standoff RDF annotation of texts with named entities (people, places, organizations).  CWRC-Writer can be used standalone, or embedded within another page.

### Standalone CWRC-Writer

![Alt Text](https://raw.githubusercontent.com/cwrc/CWRC-Writer-Reference-Implementation/master/docs/images/editor.png)

Either standalone or embedded, CWRC-Writer interacts with outside services including:

 - a document store ( to list, create, retrieve, edit, delete documents)
 - an annotation store ( to store and retrieve standoff annotations for specific documents)
 - an XML validation service
 - an entity lookup and authoring service (to lookup linked data URIs for people, place, and organizations and to create new URIs for new entities)
 - an XML schema or schemas
 - and XML template store

The CWRC-Writer interacts with the outside services by delegating calls (to list documents, for example) through one of two APIs:

- 'Delegator' -- client-side (in the browser javascript)
- RESTful -- server-side

For example, if the user clicks the button within the editor to list documents available for edit, a call is made via the delegator to the server side RESTful API:

![Alt Text](https://raw.githubusercontent.com/cwrc/CWRC-Writer-Reference-Implementation/master/docs/images/delegation.png)

A project adopting CWRC-Writer might, therefore, chose to implement a server-side API that works with the default delegator, or they may chose to implement their own delegator that can call to any service with any server side API, and then simply tranform the result within the delegator before passing it back to the CWRC-Writer.  We anticipate that most projects will implement their own delegators as they'll likely already have their own document store with it's own API.

If the CWRC-Writer is embedded within another page, the surrounding page may take care of some things like listing documents, retrieving documents, or even saving documents, in which case the surrounding page will simply pass documents to and from the CWRC-Writer for edit.  In other words, the user would no longer click the 'documents' button within the editor, but instead browse a list of documents in some list that sits outside the editor, choosing a document from that list, which is then passed into the editor by the surrounding code.  The CWRC-Writer will still instigate calls to some of the other services like the annotation store, validation service, etc., but will continue to call those services through a delegator.  

Herein we define both APIs and provide a reference implementation for both APIs, including the full suite of server side services.  The reference implementation is intended for evaluation of the CWRC-Writer and not for production use.

We intend to provide a Docker instance for ease of use.

In a separate project we provide alternate 'delegators' and associated server-side API stubs, developed together with partner projects, that can be used to ease the work of linking the CWRC-Writer to other backend services.

