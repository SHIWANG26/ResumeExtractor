 Resume Parsing Java Web Application

This is a Java-based web application designed to parse resumes (in PDF, DOCX, or plain text formats) and extract structured information such as skills, educational qualifications, work experience, and other relevant metadata. The application is built using Java Servlets and integrates several key libraries to process and analyze the content of uploaded resumes.



 Key Features

* Resume Parsing via HTTP Interface: The application exposes a servlet-based endpoint (`ResumeExtractServlet`) capable of handling both `GET` and `POST` HTTP requests. Users can upload resumes via web forms or REST clients, and the servlet processes the uploaded content.

* Natural Language Processing (NLP):
  Utilizes Apache OpenNLP, an open-source machine learning-based toolkit for processing natural language text. It is employed to:

  * Tokenize text content
  * Extract named entities (like names, dates, locations)
  * Recognize skills and job-specific terms using custom models or pattern matching

* File Format Support:

  * PDF Parsing: Uses Apache PDFBox to read and extract text from PDF resume files. PDFBox ensures accurate conversion of multi-column layouts and preserves the logical flow of content.
  * DOCX Parsing: Uses Apache POI to parse and extract text from Microsoft Word documents. Apache POI supports both `.doc` and `.docx` file formats and is robust in handling complex document structures.
  * Text File Support: Plain `.txt` resumes are processed directly using standard Java I/O libraries.



 Technology Stack

| Component     | Technology                              |
| - |  |
| Backend       | Java Servlets (javax.servlet.http)      |
| NLP Engine    | Apache OpenNLP                          |
| PDF Parser    | Apache PDFBox                           |
| Word Parser   | Apache POI (HWPF/XWPF)                  |
| File Handling | Java IO/NIO                             |
| Web Server    | Servlet container (e.g., Apache Tomcat) |



 Core Logic Overview

Class: `ResumeExtractServlet`
Package: `in.servlets`

This servlet is responsible for handling incoming resume upload requests. The resume content is expected to be passed as a request parameter or file input (this part can be enhanced further with multipart/form-data handling). The servlet responds with an HTML page displaying the extracted or submitted content (currently placeholder).

# Servlet Lifecycle Methods Implemented:

* `doGet()` and `doPost()` delegate to `processRequest()`
* `processRequest()` reads input, sets the response type, and generates HTML output
* Integration with NLP and parsing libraries is expected to be implemented beyond the placeholder



 Next Steps / Enhancements

* Implement file upload handling using `MultipartConfig` or Apache Commons FileUpload
* Add backend integration with OpenNLP models for skill/entity extraction
* Format parsed data into structured formats like JSON or XML
* Optionally integrate a database to store parsed resume content for search or analytics
* Implement a frontend interface for user-friendly resume upload and result visualization



 Dependencies

Ensure the following libraries are added to your project via Maven or manually in your build path:

```xml
<!-- Apache OpenNLP -->
<dependency>
    <groupId>org.apache.opennlp</groupId>
    <artifactId>opennlp-tools</artifactId>
    <version>1.9.4</version>
</dependency>

<!-- Apache PDFBox -->
<dependency>
    <groupId>org.apache.pdfbox</groupId>
    <artifactId>pdfbox</artifactId>
    <version>2.0.27</version>
</dependency>

<!-- Apache POI for Word Files -->
<dependency>
    <groupId>org.apache.poi</groupId>
    <artifactId>poi-ooxml</artifactId>
    <version>5.2.3</version>
</dependency>

