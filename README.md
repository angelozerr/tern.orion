tern.orion
========

[tern.js](https://github.com/marijnh/tern) is a stand-alone code-analysis engine for JavaScript written in Javascript.

[Orion](http://www.eclipse.org/orion/) is an Open Source Platform For Cloud Based Development. It provides a standalone code editor written in JavaScript (built-editor.js and built-editor.css).

**tern.orion** gives you the capability to use [tern.js](https://github.com/marijnh/tern) in a [Orion](http://www.eclipse.org/orion/) editor like the [CodeMirror Tern addon](http://ternjs.net/doc/demo.html)

Note that Orion could be interested to integrate Tern. See [bug 432940](https://bugs.eclipse.org/bugs/show_bug.cgi?id=432940)

You can find too an [Eclipse IDE wizard](https://github.com/angelozerr/tern.java/wiki/Tern-Toolings#wizard-for-tern-with-orion) which generates Orion editor with Tern.

# Features

## Completion 

If you open completion, on Array variable, you will see functions of the array : 

![Tern Orion Completion](https://github.com/angelozerr/tern.orion/wiki/images/TernOrion_CompletionOverview.png)

If you apply the completion, it will generate the signature of the selected function : 

![Tern Orion Completion Apply](https://github.com/angelozerr/tern.orion/wiki/images/TernOrion_CompletionApply.png)

Use tab, to switch to next parameter.

See [here](https://github.com/angelozerr/tern.orion/wiki/Tern-Completions) for more samples of completion (jQuery, Angular, etc).

# How to use it?

Import in your HTML page : 

 * Orion editor built-editor.js and built-editor.css
 * [tern-orion.js](https://github.com/angelozerr/tern.orion/blob/master/lib/tern-orion.js)

Create Orion editor and add tern completion : 

	require(["orion/editor/edit", "orion/tern/ternServer"], function(edit, mTernServer) {
		var editor = edit({
			lang: "js"
		});

		// tern server
		var defs = []; // load defs
		var plugins = {}; // load plugins
		var ternServer = new mTernServer.TernServer({defs: defs, plugins: plugins});

		// tern completion
		ternServer.addContentAssistProvider(editor);
	});
	
# Structure

The basic structure of the project is given in the following way:

* `demos/` demos with Tern and Orion. Open tern-orion.html.
* `lib/` contains `tern-orion.js` which is the glue between Tern and Orion.
