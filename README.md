# idea-js-quickdoc-nowrap

## English
Example of generated documentation from `JSDocumentationProvider`
```html
<div class='definition'>
	<pre>TagNormalizer.denormalizeTags(<br>    tags: <a href="psi_element://NormalizedTags">NormalizedTags</a>): <a
			href="psi_element://Vector">Vector</a>&lt;<a href="psi_element://ApiTag">ApiTag</a>&gt;</pre>
</div>
<div class='content'><p>De-normalizza una lista di tag.
	<p>Questo step e' necessario per l'invio delle informazioni al back-end,
	<p>oppure per i componenti Angular che hanno necessita' di una
	<p>struttura dati innestata.</div>
<table class='sections'>
	<tr>
		<td valign='top' class='section'><p>Params:</td>
		<td valign='top'><p>tags &ndash; I tag da de-normalizzare
</table>
```

* class `JSDocBuildMethodInfo extends JSDocBuilderSymbolInfo`<br>
  the HTML string is built here
* method `JSDocBuilderSymbolInfo#addContent`<br>
  the body of the quickdoc (the main content) is created here
* method `JSDocBuilderSimpleInfo#convertMarkdownToHtml`<br>
  every `\n` is suffixed with a `<p>` tag here. The paragraph represents the wrap
	
The route to take seems to be:
* extend `JSDocumentationProvider`, overriding  method `generateDoc` to use the cloned class mentioned below
* clone `JSDocumentationBuilder`, editing the constructor to use the new classes mentioned below
* extend `JSDocBuilderMethodInfo` and `JSDocBuilderSymbolInfo`, overriding method `convertMarkdownToHtml`
* use the new classes in place of the old (standard) ones in `JSDocumentationBuilder`

## Italiano
Esempio di stringa generata da `JSDocumentationProvider`
```html
<div class='definition'>
	<pre>TagNormalizer.denormalizeTags(<br>    tags: <a href="psi_element://NormalizedTags">NormalizedTags</a>): <a
			href="psi_element://Vector">Vector</a>&lt;<a href="psi_element://ApiTag">ApiTag</a>&gt;</pre>
</div>
<div class='content'><p>De-normalizza una lista di tag.
	<p>Questo step e' necessario per l'invio delle informazioni al back-end,
	<p>oppure per i componenti Angular che hanno necessita' di una
	<p>struttura dati innestata.</div>
<table class='sections'>
	<tr>
		<td valign='top' class='section'><p>Params:</td>
		<td valign='top'><p>tags &ndash; I tag da de-normalizzare
</table>
```

* classe `JSDocBuildMethodInfo extends JSDocBuilderSymbolInfo`<br>
  qui viene creata la stringa HTML
* metodo `JSDocBuilderSymbolInfo#addContent`<br>
  qui viene creato il body del quickdoc
* metodo `JSDocBuilderSimpleInfo#convertMarkdownToHtml`<br>
  qui vengono inseriti i tag `<p>` per ogni `\n`, che sono il wrap
	
La strada da prendere sembra quella di:
* estendere `JSDocumentationProvider`, sovrascrivendo il metodo `generateDoc` per utilizzare la nuova classe clonata menzionata sotto
* clonare `JSDocumentationBuilder`, modificando il costruttore per utilizzare le nuove classi menzionate sotto
* estendere `JSDocBuilderMethodInfo` e `JSDocBuilderSymbolInfo`, sovrascrivendo il metodo `convertMarkdownToHtml`
* utilizzare le nuove classi al posto delle "vecchie" (standard) in `JSDocumentationBuilder`
