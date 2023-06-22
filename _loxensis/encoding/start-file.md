---
layout: default
title: The start files
parent: Encoding manual
permalink: /loxensis/encoding/start-file
nav_order: 1
---

# The start files #

## What do you need for the encoding? ##

{: .highlight }
A paragraph

Example
## Start file ##

	<?xml version="1.0" encoding="UTF-8"?>
	<TEI xmlns="http://www.tei-c.org/ns/1.0">
	    <teiHeader>
	        <fileDesc>
	            <titleStmt>
	                <title><!-- title of the text --></title> 
	                <author><!-- author of the text --></author> 
	            </titleStmt>
	            <publicationStmt>
	                <p corresp="session"><!-- # of the session --></p> 
	                <p corresp="version"><!-- # of the text-version --></p> 
	                <p corresp="total_versions"><!-- total # of versions or sessions --></p> 
	            </publicationStmt>
	            <sourceDesc>
	                <p>
	                    <l><!-- Date of the writing session --></l> 
	                    <l><!-- Start-time of the writing session --></l> 
	                    <l><!-- Duration of the writing session --></l> 
	                </p>
	            </sourceDesc>
	        </fileDesc>
	    </teiHeader>
	    <text>
	        <body>
	            <p source="keystrokes">  
	            	<!-- Encode the writing process of the text here -->  
	            </p>
	            <p source="sources"> 
	            	<!-- Encode the sources here -->   
	            </p>
	            <p source="notes"> 
	            	<!-- Encode possible editor notes here -->   
	            </p>
	        </body>
	    </text>
	</TEI>

