Karthic's Blog
---

- ###Markdown Syntax: Things to keep in mind
	- Block level HTML elements like \<div\>, \<table\>, \<pre\>, \<p\> must be separated from surrounding content by blank lines and the start of the tags shouldn't be indented
	- Markdown syntax like *emphasis* is not processed within block level HTML Tags
	- Markdown syntax is processed in non-block level tags like \<span\>
	- Markdown automatically escapes characters like < and &
	- Paragraphs are separated from other paragraphs with a blank line. To insert a blank line, end the paragraph with 2 spaces  
	and then hit return
	- To insert blockquotes within a list item, the blockquote delimiter \> must be indented
		> Like this
		
	- Code spans need to be indented twice  
	
			int main()
	- 

- ###PHP Markdown Extra and Other Markdown Implementation Features
	- Adapted from PHP Markdown Extra <https://michelf.ca/projects/php-markdown/extra/>
	- Additions to Markdown
		- Block level html tags need not be indented
		- Can add a statement like  
		
				<div markdown = "1">
				This is *true* markdown
				</div>
		  and the text will be formatted according to markdown syntac
		-  Special Attributes
			- Can set the id and class attribute on certain elemnts using an attribute block
			- For example
					
					Header 1	{#header1}
			Then you can create links back to different parts of the same document like this:
					
				[Link back to header1](#header1)
				
			- To add a class name, which can be used by a style sheet use a dot like this:
			
					## This site ## {.main}
					
				(or)
				
					## This site ## {lang = fr}
					
			- Combining it all
					
					## Le Site ## {.main #LeSite}
					
			- *Special attribute blocks can only be used with the following*
				- headers
				- fenced code blocks (```)
				- links
				- images 
			- As far as I could find, there was only two examples of including other files in your markdown document done both by other third-party softwares:
				- markdown-include: a nodejs application that included files like this:
					
						#include "markdown-file.md"
						
				- Marked: a MultiMarkdown preview application that included files like this:
				
						<<[file.md]
						
- ###Propsed Syntax for adding links to regions within a page
	- Use the syntax ```{#link-name}``` at the end of a line (should be followed only by whitespace)
	- When processed, this will translate to the html tag
	
			<a name="link-name">
		that will be placed at the start of that line. It cannot be indented by more than 4 spaces if it is the only text in a line. If it is indented by more than 4 spaces then it is treated as code
	- When you want to reference to that link within the page you can use either of the following syntaxes
	
		1.	```<#link-name>{...}``` which will be translated into html as 
		 	
				<a href="#link-name">link-name(Note no # here)</a>{...}
		
		2. ```[Link-Title](#link-name){...}``` which will be translated into html as
		 
				<a href="#link-name">Link-Title</a>{...}
		 		
	- References to links within the page will be treated just like regular links. If we want to type {#link-name} without making a reference to a link, we can choose to backslash escape that
	- Creating references to a link (by using ```{#link-name}``` to generate the ```<a name="link-name">```) can only occur at the end of a line and can be followed only by whitespace 
		 

			
			
						
			
					
		 
	

