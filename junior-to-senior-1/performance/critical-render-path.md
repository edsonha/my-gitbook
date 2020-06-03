# Critical Render Path

HTML

* Load style tag in the &lt;head&gt;
* Load script right before &lt;/body&gt; to be non-blocking

CSS

* Only load whatever is needed. Load only css files that you need
* Above the fold loading... Only render the one is shown on the page 
* Media attributes
* Less specificity in CSS

JS

* Load script asynchronously \(Download script while HTML is parsing. But still paused the HTML parsing during script execution. So it is best to be used for something that is non essential to the user experience. Like Google analytics scripts or tracking scripts.
* Defer loading of scripts \(Download script while HTML is parsing and the execution happen after the HTML finish parsing\)
* Minimize DOM Manipulation
* Avoid long running JS

