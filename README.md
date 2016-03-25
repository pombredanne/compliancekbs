# compliancekbs
Compliance Knowledge Base Service for Security Controls Compliance Server

API server
----------

    pip3 install -r requirements.txt
    python3 server.py

YAML schema
-----------

### documnet

Each YAML file describes a document. Documents have the following fields:

`id`: An identifier for this document unique within the GovReady Knowledge Base.

`title`: The display title of the document.

`document-cloud-id`: If the document is uploaded to Document Cloud, then the id of the document on Document Cloud. For the document at https://www.documentcloud.org/documents/2752694-NIST-SP-800-53r4.html, the `document-cloud-id` is just `2752694-NIST-SP-800-53r4`.

`url`: If the document is not in Document Cloud, a URL where the document can be viewed.

`format`: If the document is not in Document Cloud, the document's format. Can be `markdown`.

`terms`: An array of one or more terms found in the document (see below).

### term

A term is a phrase that appears in a document. It has the following attributes:

`term`: The text as it appears in the document.

`page`: The primary page on which it appears in the document (e.g. where it is defined, if applicable).

`role`: This attribute has the value `definition` if the term is defined within this document.

`defined-by`: A `term-reference` (see below) to where this term is defined.

`same-as`: A `term-reference` (see below) to another term that has the same meaning.

### term-reference

A term-reference is a way of locating a term within a document. A term-reference has the following attributes:

`document`: The identifier (`id`) of the document where the referenced term occurs. If this attribute is missing, then a term is being referenced in the same document that the YAML file is describing --- i.e. to `same-as` two terms that appear in the same document.

`term`: The text of the term as it appears in that document. 
