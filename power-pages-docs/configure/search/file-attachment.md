---
title: Search within knowledge article attachment content
description: Learn how to configure your Power Pages site to search within file attachment content.
author: nageshbhat-msft

ms.topic: conceptual
ms.custom: 
ms.date: 1/23/2023
ms.subservice:
ms.author: nabha
ms.reviewer: dmartens
contributors:
    - sandhangitmsft
    - nageshbhat-msft
---

# Search within knowledge article attachment content

You can use the knowledge article attachment to include downloadable files in knowledge base articles. You can also use web files to create an FAQ page with downloadable content.

> [!IMPORTANT]
> Only the files that are attached to knowledge articles can be searched. The files that are attached to web files are not searchable.

You can configure your Power Pages site to allow users to search within the attachment content of  knowledge base articles. This helps users to find the information that they're looking for.

In knowledge base articles, any attachment with the defined prefix is indexed.

To index the knowledge article attachments, you must create the following site settings and set their value to **True**:

|Site setting|Description|
|------------|-----------|
|Search/IndexNotesAttachments|Indicates whether the content of attachments in knowledge base articles should be indexed. By default, it's set to **False**.|
|KnowledgeManagement/DisplayNotes|Indicates whether to display attachments of knowledge base articles. By default, it's set to **False**.|
|||

When you search for a term, the search results also include attachments. If the search term matches a knowledgearticle attachment, the link to the corresponding knowledge base article is also provided. To see downloadable attachments, select **Downloads** under **Record Type** in the left pane. To modify the **Downloads** label, edit the Search/Facet/Downloads content snippet. By default, the value is set to **Downloads**.

> [!NOTE]
> [Dataverse search](/power-platform/admin/configure-relevance-search-organization) must be enabled in your environment to use this functionality.

### Search through knowledge article attachments

If your site uses Lucene .NET [search](overview.md), you can enable the website to search through knowledge article attachments by setting the **Sync knowledge article attachments to site** option to **Yes** in the Dynamics 365 Customer Service admin center or Customer Service Hub app. You don't need to configure this option if your site is using Dataverse search, you'll be able to search through knowledge article attachments by default.

This allows search to look through knowledge article attachments and make information easily accessible to knowledge consumers. With this attachment capability, you won’t need to use the notes attachments for the site. Knowledge article attachments will automatically be synced to the notes attachment. More information: [Update knowledge article attachments for portal](/dynamics365/customer-service/customer-service-hub-user-guide-knowledge-article?tabs=customerserviceadmincenter#update-knowledge-article-attachments-for-portal)

## Update site configurations

If you already have a website before April 2018 and you've upgraded your site to the latest version, you must use the following configurations to have the same user experience as a new installation.

### Content Snippets

To modify the label displayed in the search results for annotation and web file downloads, create a content snippet Search/Facet/Downloads, and then set its value as required. The default value is **Downloads**.

### Web Templates

The Faceted Search - Results Template web template is revised to display files associated with knowledge base articles as primary search result items with a related article link. You must update the Faceted Search - Results Template web template to the following source:

```
{% assign openTag = '{{' %}
{% assign closingTag = '}}' %}
{%raw%}
  <script id="search-view-results" type="text/x-handlebars-template">
    {{#if items}}
      <div class="page-header">
        <h2>{%endraw%}{{openTag}} stringFormat "{{ resx.Search_Results_Format_String }}" firstResultNumber lastResultNumber itemCount {{closingTag}}{%raw%}
          <em class="querytext">{{{query}}}</em>
          {{#if isResetVisible}}
            <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
          {{/if}}
        </h2>
      </div>
      <ul>
        {{#each items}}
          <li>
            <h3><a title="{{title}}" href="{{url}}">{{#if parent}}<span class="glyphicon glyphicon-file pull-left text-muted" aria-hidden="true"></span>{{/if}}{{title}}</a></h3>
            <p class="fragment">{{{fragment}}}</p>
            {{#if parent}}
              <p class="small related-article">{%endraw%}{{ resx.Related_Article }}{%raw%}: <a title="{{parent.title}}" href="{{parent.absoluteUrl}}">{{parent.title}}</a></p>
            {{/if}}
            <ul class="note-group small list-unstyled">
            {{#if relatedNotes}}
              {{#each relatedNotes}}
                <li class="note-item">
                  {{#if isImage}}
                    <a target="_blank" title="{{title}}" href="{{absoluteUrl}}"><span class="glyphicon glyphicon-file" aria-hidden="true"></span>&nbsp;{{title}}</a>
                  {{else}}
                    <a title="{{title}}" href="{{absoluteUrl}}"><span class="glyphicon glyphicon-file" aria-hidden="true"></span>&nbsp;{{title}}</a>
                  {{/if}}
                  <p class="fragment text-muted">{{{fragment}}}</p>
                </li>
              {{/each}}
            {{/if}}
            {{#if relatedAttachments}}
              {{#each relatedAttachments}}
                <li class="note-item">
                  {{#if isImage}}
                    <a id="kbattachment-{{entityID}}" href="javascript:downloadKbAttachmentFile('kbattachment-{{entityID}}', '{{title}}', {{fileSize}}, '{{fileType}}', '{{downloadBlockUrl}}', '{{initializeDownloadUrl}}')"><span class="glyphicon glyphicon-file" aria-hidden="true"></span>&nbsp;{{title}}</a>
                  {{else}}
                    <a id="kbattachment-{{entityID}}" title="{{title}}" href="javascript:downloadKbAttachmentFile('kbattachment-{{entityID}}', '{{title}}', {{fileSize}}, '{{fileType}}', '{{downloadBlockUrl}}', '{{initializeDownloadUrl}}')"><span class="glyphicon glyphicon-file" aria-hidden="true"></span>&nbsp;{{title}}</a>
                  {{/if}}
                  <p class="fragment text-muted">{{{fragment}}}</p>
                </li>
              {{/each}}
            {{/if}}
            </ul>
          </li>
        {{/each}}
      </ul>
    {{else}}
      <h2>{%endraw%}{{ resx.Search_No_Results_Found }}{%raw%}<em class="querytext">{{{query}}}</em>
        {{#if isResetVisible}}
          <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
        {{/if}}
      </h2>
   {{/if}}
  </script>
  <script type="text/javascript">
    function downloadKbAttachmentFile(attachmentElementId, fileName, fileSize, mimeType, downloadBlockUrl, initializeUrl) {
      // Download block API supports max 4MB block size
      const blockSizeInBytes = 4096 * 1024;
      const totalNumberOfBlocks = parseInt(fileSize / blockSizeInBytes + 1);
      var fileContinuationToken = "";
      var contentString = "";
      var numberOfBlocksDownloaded = 0;
      var blockNumberToContentMap = {};
      function downloadBlockCallback(i, result) {
        numberOfBlocksDownloaded++;
        blockNumberToContentMap[i] = result;
        if (numberOfBlocksDownloaded == totalNumberOfBlocks) {
          for (var j = 0; j < totalNumberOfBlocks; j++) {
            contentString += blockNumberToContentMap[j];
          }
          var isImage = mimeType.startsWith('image/');
          const attachmentElement = document.getElementById(attachmentElementId);
          if (isImage) {
            const bodyByteString = atob(contentString);
            const bodyBuffer = new ArrayBuffer(bodyByteString.length);
            const bodyView = new Uint8Array(bodyBuffer);
            for (var k = 0; k < bodyByteString.length; k++) {
              bodyView[k] = bodyByteString.charCodeAt(k);
            }
            var imageUrl = URL.createObjectURL(new Blob([bodyBuffer], { type: mimeType }));
            attachmentElement.href = imageUrl;
            attachmentElement.target = "_blank";
          }
          else {
            const linkSource = 'data:' + mimeType + ';base64,' + contentString;
            attachmentElement.href = linkSource;
            attachmentElement.download = fileName;
          }
          attachmentElement.click();
        }
      }
      shell.ajaxSafePost({
        type: 'GET',
        url: initializeUrl,
        success: function (result) {
          fileContinuationToken = encodeURIComponent(result);
          for (var i = 0; i < totalNumberOfBlocks; i++) {
            url = downloadBlockUrl + "&blockNumber=" + i + "&fileContinuationToken=" + fileContinuationToken + "&blockSize=" + blockSizeInBytes;
            var x = downloadBlockCallback.bind(this,i);
            shell.ajaxSafePost({
              type: 'GET',
              url: url,
              success: (result) => { x(result) }
            });
          }
        }
      });
    }
  </script>
{%endraw%}
```

### Site Settings

You must add `\_logicalname:annotation~0.9^0.25` value to the Search/Query site setting. After it's added, the value should be as follows:
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

To configure the facets to group annotations associated with knowledge base articles and web files in a single facet, edit the Search/RecordTypeFacetsEntities site setting name and append `;Downloads:annotation,adx_webfile` to its value.

To allow attachments associated with knowledge articles to appear in the website and search results, edit the **KnowledgeManagement/DisplayNotes** site setting and set its value to **True**. The site setting **KnowledgeManagement/NotesFilter** contains a prefix value that must be prefixed to the note text field on notes; only notes with the specified prefix value will appear on the webpage. By default, the value is \*WEB\*, but you can change it through the site setting.

To enable the indexing of file attachments associated with notes, create the **Search/IndexNotesAttachments** site setting and set its value to **True**.

