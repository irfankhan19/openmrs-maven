1. DWR-2.0.5 Patch


I've made two modifications for our use of dwr.

The first was a result of dwr removing functionality that we were depending on.

In the second, I'm adding attributes to facilitate modules.  I made the change
to the doctype just so errors would disappear.


Modified \java\uk\ltd\getahead\dwr\util.js :
 - Replaced 1085:1099:
    var td = options.cellCreator(options);
    if (td != null) {
      if (options.data != null) {
        if (dwr.util._isHTMLElement(options.data)) td.appendChild(options.data);
        else {
          if (dwr.util._shouldEscapeHtml(options) && typeof(options.data) == "string") {
            td.innerHTML = dwr.util.escapeHtml(options.data);
          }
          else {
            td.innerHTML = options.data;
          }
        }
      }
      tr.appendChild(td);
    }

    with this:
    if (dwr.util._isHTMLElement(options.data, "td")) {
       tr.appendChild(options.data);
    }
    else {
      var td = options.cellCreator(options);
      if (td != null) {
        if (options.data != null) {
          if (dwr.util._isHTMLElement(options.data)) td.appendChild(options.data);
          else {
            if (dwr.util._shouldEscapeHtml(options) && typeof(options.data) == "string") {
              td.innerHTML = dwr.util.escapeHtml(options.data);
            }
             else {
              td.innerHTML = options.data;
            }
          }
        }
        tr.appendChild(td);
      }
    }


Modified both "/org/directwebremoting/dwr10.dtd" and "/org/directwebremoting/dwr20.dtd":
 - Added
    <!ATTLIST signatures
     moduleId CDATA #IMPLIED
    >

 - Added
    <!ATTLIST allow
     moduleId CDATA #IMPLIED
    >


2. HIBERNATE-2.3.5 Patch

There is 1 change to the hibernate jar file:

See hibernate.patch in this folder.

1) http://dev.openmrs.org/ticket/1131 "ConceptService.saveConcept should allow you to create
   a concept with a specified concept id"

   This Hibernate forum post has more information on the patch committed:
   http://forum.hibernate.org/viewtopic.php?p=2400324


3. LIQUIBASE-1.9.4 PATCH

The liquibase 1.9.4 patch contains these modifications:

1) Added GroupedChange so that exporting of xml files is smaller in size (only used when dumping databases into xml changelog files)

2) Added attribute to generateChangeLog ant task to allow for passing in of diffTypes argument

3) Modified indexExists and columnExists to speed up preconditions - http://dev.openmrs.org/ticket/1719


4. SIMPLE-XML-1.6.1 PATCH

