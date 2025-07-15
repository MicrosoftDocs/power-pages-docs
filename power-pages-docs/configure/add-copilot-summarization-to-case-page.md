---
title: Add Copilot summarization to case page (Preview)
description: Learn how to add Copilot summarization to the case page in Power Pages.
author: nageshbhat-msft
ms.topic: how-to
ms.date: 06/27/2025
ms.author: nabha
ms.reviewer: dmartens
ms.collection:
 - bap-ai-copilot
contributors:
    - dmartens
    - tapanm
---

# Add Copilot summarization to case page (preview)

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-banner.md)]

This guide explains how to set up the Copilot summarization section for the support case page so users can quickly review a case and its timeline summary.

[!INCLUDE [file-name](~/../shared-content/shared/preview-includes/preview-note-pp.md)]

## Prerequisites

Use the site created with the [Community](/power-pages/templates/dynamics-365-apps/overview?WT.mc_id=powerportals_inproduct_portalstudio2#community) or [Customer self-service](/power-pages/templates/dynamics-365-apps/overview?WT.mc_id=powerportals_inproduct_portalstudio2#customer-self-service) portal template. These portals include the support case page.

## Step 1 - Create site settings

Before using the data summarization API, use the Portal Management app to enable the required site settings.

1. Open the [Portal Management app](/power-pages/configure/portal-management-app).
1. On the selected website record, select **Site Settings**.
1. Enter the following site settings and values.

    | Setting description | Name | Value |
    |---------------------|------|-------|
    | Enable the summarization API. | Summarization/Data/Enable | true |
    | Set the summarization prompt. | Summarization/prompt/case_summary | "Summarize key details and critical information" |
    | Enable the Web API for the case table. | Webapi/incident/enabled | true |
    | Enable description and title fields of the case table. | Webapi/incident/fields | description,title |
    | Enable the portal comments table for the web API. | Webapi/adx_portalcomment/enabled  | true |
    | Enable the description field of the portal comments table. | Webapi/adx_portalcomment/fields | description |

## Step 2 - Add the Copilot summary section

In this step, you add a summary section at the top of the case page.

1. Open [Power Pages studio](https://make.powerpages.microsoft.com).
1. Select **Edit** for the site that you want to edit.
1. Select **Customer Service - Edit Case**.

    On this page, you add a summary section.

1. Select **Edit code** to open Visual Studio Code.
1. Copy the following code, and add it to the beginning of the code block.

    ```html
    <!DOCTYPE html>
    <html lang="en">
      <head></head>
      <body>
        <style>
          .collapsible {
            color: #444;
            cursor: pointer;
            padding: 10px;
            width: 100%;
            text-align: left;
            outline: none;
            font-size: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: none;
            background: none;
          }
    
          .active,
          .collapsible:hover {
            background-color: #ccc;
          }
    
          .content {
            padding: 0 18px;
            display: none;
            overflow: hidden;
          }
    
          .chevron {
            border: solid #666;
            border-width: 0 3px 3px 0;
            display: inline-block;
            padding: 5px;
            transform: rotate(45deg);
            /* Right-pointing chevron */
            transition: transform 0.3s ease;
          }
    
          .chevron.collapsed {
            transform: rotate(-135deg);
            /* Downward-pointing chevron */
          }
    
          /* Add overflow hidden to the parent container */
          .Summarizationcontainer {
            border: 2px solid transparent;
            /* Set a transparent border */
            border-radius: 4px;
            /* Adjust the value as needed */
            width: auto;
            overflow: hidden;
            /* Ensure content stays within the rounded corners */
            padding: 5px;
            background: white;
            /* Background color of the container */
            border-image: linear-gradient(90deg, rgb(70, 79, 235) 35%, rgb(71, 207, 250) 70%, rgb(180, 124, 248) 92%) 1;
            /* Adjust the slice value */
            -webkit-mask-image: -webkit-radial-gradient(white, black);
            /* Ensure the border image respects the border-radius */
            mask-image: radial-gradient(white, black);
            /* Ensure compatibility with other browsers */
          }
    
          #control {
            max-width: 100%;
            height: fit-content;
            display: flex;
            justify-content: space-between;
            align-items: center;
          }
    
          .flex-container {
            display: flex;
            width: 100%;
            padding-left: 5px;
            justify-content: space-between;
            align-items: center;
            /* Keep this */
            gap: 5px;
            /* Add this to add spacing between icon and text */
          }
    
          .flex-container svg {
            vertical-align: middle;
            /* Ensure icon is aligned with the text */
          }
    
          .chevron-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100%;
          }
    
          .copy-btn {
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 4px;
            padding: 8px 12px;
            display: inline-flex;
            align-items: center;
            cursor: pointer;
            font-size: 14px;
          }
    
          .shimmer {
            height: 10px;
            background: linear-gradient(90deg, #f0f0f0 25%, #e0e0e0 50%, #f0f0f0 75%);
            background-size: 200% 100%;
            animation: shimmer 1.5s infinite;
          }
    
          @keyframes shimmer {
            0% {
              background-position: -200% 0;
            }
    
            100% {
              background-position: 200% 0;
            }
          }
        </style>
        <br>
        <br>
        <div class="Summarizationcontainer" style="height: fit-content;    ">
          <div id="control">
            <div class="flex-container">
              <div style="display: inline-block; font-size: larger;">
                <svg width="22" height="23" viewBox="0 0 22 23" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M7.06063 15.9471C7.33535 16.1416 7.66359 16.2462 8.00018 16.2464C8.31642 16.2463 8.62578 16.154 8.8904 15.9809C9.15503 15.8077 9.36345 15.5612 9.49018 15.2714L10.2592 12.9314C10.4468 12.3685 10.7629 11.8569 11.1824 11.4373C11.6019 11.0176 12.1133 10.7013 12.6762 10.5134L14.9142 9.78642C15.2319 9.67509 15.5068 9.46701 15.7002 9.19142C15.8489 8.98202 15.9457 8.74029 15.9826 8.48614C16.0195 8.232 15.9956 7.97271 15.9127 7.72965C15.8298 7.48658 15.6903 7.26669 15.5057 7.0881C15.3212 6.9095 15.0968 6.77732 14.8512 6.70242L12.6362 5.98242C12.073 5.79569 11.5611 5.4803 11.141 5.06128C10.721 4.64226 10.4043 4.13113 10.2162 3.56842L9.48918 1.33142C9.37728 1.01454 9.16972 0.740235 8.89518 0.546422C8.61891 0.355921 8.29126 0.253906 7.95568 0.253906C7.6201 0.253906 7.29245 0.355921 7.01618 0.546422C6.73716 0.743489 6.52724 1.02338 6.41618 1.34642L5.67918 3.61142C5.49149 4.1594 5.18155 4.65749 4.77284 5.06793C4.36413 5.47838 3.86736 5.79042 3.32018 5.98042L1.08018 6.70742C0.761438 6.82009 0.485742 7.02931 0.291448 7.30598C0.0971552 7.58264 -0.00607216 7.91298 -0.00387179 8.25104C-0.00167166 8.58911 0.105847 8.91808 0.303725 9.19218C0.501603 9.46629 0.779999 9.67191 1.10018 9.78042L3.31618 10.4994C3.8811 10.6883 4.39454 11.0057 4.81618 11.4264C4.92914 11.5395 5.0347 11.6598 5.13218 11.7864C5.39803 12.1289 5.60301 12.5145 5.73818 12.9264L6.46618 15.1604C6.57824 15.4778 6.78592 15.7527 7.06063 15.9471ZM16.8043 22.0276C17.0078 22.1709 17.2509 22.2474 17.4999 22.2464C17.7473 22.2475 17.989 22.1721 18.1919 22.0304C18.4002 21.8826 18.5563 21.6725 18.6379 21.4304L19.0099 20.2874C19.0885 20.0501 19.2214 19.8344 19.3979 19.6574C19.5745 19.4803 19.7898 19.3468 20.0269 19.2674L21.1929 18.8894C21.4284 18.8058 21.6324 18.6514 21.7769 18.4474C21.9218 18.2441 21.9997 18.0006 21.9997 17.7509C21.9997 17.5012 21.9218 17.2578 21.7769 17.0544C21.6232 16.8422 21.4056 16.6848 21.1559 16.6054L20.0119 16.2344C19.7746 16.1558 19.5588 16.0229 19.3818 15.8464C19.2047 15.6698 19.0712 15.4545 18.9919 15.2174L18.6129 14.0544C18.5311 13.8167 18.3768 13.6107 18.1717 13.4654C17.9666 13.32 17.721 13.2428 17.4696 13.2446C17.2182 13.2464 16.9738 13.327 16.7707 13.4752C16.5676 13.6234 16.4162 13.8316 16.3379 14.0704L15.9639 15.2164C15.8873 15.4507 15.7579 15.6642 15.5858 15.8405C15.4136 16.0169 15.2032 16.1513 14.9709 16.2334L13.8049 16.6114C13.5693 16.6951 13.3653 16.8495 13.2209 17.0534C13.0759 17.2568 12.998 17.5002 12.998 17.7499C12.998 17.9996 13.0759 18.2431 13.2209 18.4464C13.3695 18.6531 13.5794 18.8078 13.8209 18.8884L14.9649 19.2604C15.2032 19.3393 15.4196 19.4729 15.5969 19.6506C15.7743 19.8283 15.9075 20.045 15.9859 20.2834L16.3639 21.4464C16.4468 21.6811 16.6008 21.8842 16.8043 22.0276Z" fill="url(#paint0_linear_7812_14504)"></path>
                  <defs>
                    <linearGradient id="paint0_linear_7812_14504" x1="-0.00390625" y1="11.2502" x2="21.9997" y2="11.2502" gradientUnits="userSpaceOnUse">
                      <stop offset="0.104167" stop-color="#335CCC"></stop>
                      <stop offset="1" stop-color="#8330E9"></stop>
                    </linearGradient>
                  </defs>
                </svg> Summary
              </div>
              <div style="display: inline-block; margin-left: auto;">
                <button class="collapsible" id="title" onclick="showResult()">
                  <div class="chevron-container">
                    <div class="chevron" id="chevron"></div>
                  </div>
                </button>
              </div>
            </div>
          </div>
          <br>
          <div id="Summary_text" style="height: fit-content; display: none; padding-left: 5px;">
            <div style="width: 100%; overflow: hidden;"></div>
            <!-- Added to ensure button is above the text -->
            <div id="summary_final"></div>
            <div id="shimmer" style="display: block; width: auto;">
              <div class="shimmer"></div>
              <div class="shimmer"></div>
              <div class="shimmer"></div>
              <div class="shimmer"></div>
              <div class="shimmer"></div>
            </div>
            <br>
            <div style="display: flex;">
              <button onclick="copyText()" onmouseover="this.style.cursor = 'pointer'" style=" background: none; border: none;padding-left: 0;">
                <svg width="24" height="24" viewBox="0 0 20 21" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M6.00029 6.83134L6 13.2461C6 14.5716 7.03154 15.6561 8.33562 15.7408L8.5 15.7461L12.9144 15.7468C12.7083 16.329 12.1528 16.7461 11.5 16.7461H8C6.34315 16.7461 5 15.4029 5 13.7461V8.24609C5 7.59288 5.41754 7.03718 6.00029 6.83134ZM13.5 4.74609C14.3284 4.74609 15 5.41767 15 6.24609V13.2461C15 14.0745 14.3284 14.7461 13.5 14.7461H8.5C7.67157 14.7461 7 14.0745 7 13.2461V6.24609C7 5.41767 7.67157 4.74609 8.5 4.74609H13.5ZM13.5 5.74609H8.5C8.22386 5.74609 8 5.96995 8 6.24609V13.2461C8 13.5222 8.22386 13.7461 8.5 13.7461H13.5C13.7761 13.7461 14 13.5222 14 13.2461V6.24609C14 5.96995 13.7761 5.74609 13.5 5.74609Z" fill="#3B3A39"></path>
                </svg>
              </button>
              <div id="AIWarning" style="display: flex; align-self: start; gap: 8px; align-items: center; margin-left: auto;">
                <span>AI-generated content may be incorrect</span>
                <div style="display: flex; gap: 10px;">
                  <svg width="24" height="24" onmouseover="this.style.cursor = 'pointer'" viewBox="0 0 21 22" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M10.0349 4.66942C10.2441 4.14858 10.8301 3.58909 11.5806 3.79769C12.1709 3.96175 12.5544 4.31868 12.7735 4.79416C12.9778 5.23736 13.028 5.75903 13.0375 6.25617C13.0478 6.79093 12.9361 7.4325 12.8047 7.99361C12.7434 8.25515 12.6759 8.50726 12.6099 8.73389H13.9949C15.3298 8.73389 16.29 10.0166 15.9139 11.2974L14.5497 15.9434C14.1555 17.2858 12.7365 18.0435 11.4018 17.6242L6.04591 15.9419C5.45891 15.7575 4.98944 15.3132 4.77304 14.7372L4.25304 13.3533C3.91142 12.4441 4.27244 11.4208 5.109 10.9273L6.98089 9.82293C6.98462 9.82032 6.99002 9.81646 6.99704 9.81129C7.01761 9.79614 7.05204 9.76971 7.09835 9.73044C7.19093 9.65194 7.33128 9.52189 7.5035 9.32764C7.84755 8.93957 8.32141 8.29235 8.79565 7.28313C9.00052 6.84715 9.17287 6.50443 9.32941 6.19316C9.58243 5.69005 9.79411 5.26912 10.0349 4.66942ZM7.51946 10.6658C7.51378 10.6694 7.50805 10.673 7.50224 10.6764L5.61713 11.7886C5.19885 12.0353 5.01834 12.547 5.18915 13.0016L5.70914 14.3855C5.81735 14.6735 6.05208 14.8957 6.34558 14.9878L11.7015 16.6702C12.5023 16.9217 13.3537 16.4671 13.5902 15.6617L14.9544 11.0156C15.1424 10.3752 14.6623 9.73389 13.9949 9.73389H11.9259C11.7635 9.73389 11.6112 9.65503 11.5175 9.52241C11.4238 9.38979 11.4004 9.21992 11.4546 9.06686C11.5546 8.78478 11.7067 8.29608 11.831 7.7655C11.9571 7.22735 12.0456 6.68318 12.0377 6.2754C12.0287 5.80709 11.9791 5.45944 11.8654 5.21276C11.7665 4.99836 11.6138 4.84483 11.3128 4.76117C11.2697 4.74919 11.2195 4.75269 11.1535 4.79598C11.0815 4.84328 11.0078 4.93027 10.9629 5.04208C10.7092 5.67381 10.4665 6.15766 10.1979 6.6932C10.0431 7.00173 9.87974 7.32742 9.7007 7.70842C9.18681 8.80204 8.66067 9.52982 8.25176 9.99104C8.04749 10.2214 7.87312 10.3846 7.74509 10.4932C7.68109 10.5474 7.62875 10.588 7.59013 10.6164C7.57082 10.6307 7.55495 10.6418 7.54277 10.6502L7.5273 10.6607L7.52171 10.6643L7.51946 10.6658ZM6.97612 9.82627L6.97492 9.82706L6.97612 9.82627Z" fill="#424242"></path>
                  </svg>
                  <svg width="24" height="24" onmouseover="this.style.cursor = 'pointer'" viewBox="0 0 21 22" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12.5776 12.7456C12.5944 12.8791 12.6119 13.0309 12.6283 13.1961C12.7019 13.9354 12.7593 14.9889 12.6146 15.8735C12.5427 16.3126 12.4137 16.7602 12.1727 17.1097C11.9161 17.4818 11.526 17.7456 11.0002 17.7456C10.4836 17.7456 10.1691 17.3759 9.97616 17.0544C9.78384 16.734 9.61527 16.2991 9.44271 15.8539L9.42958 15.82C8.88287 14.4098 8.13522 12.5032 6.1232 11.1618C5.81627 10.9572 5.5248 10.81 5.26989 10.7042C4.5733 10.4154 3.94781 9.64714 4.11258 8.76775L4.33656 7.57236C4.47706 6.82247 5.03196 6.21785 5.76706 6.01365L10.7171 4.63863C12.6934 4.08968 14.716 5.35001 15.0939 7.36594L15.5475 9.78489C15.836 11.3234 14.6557 12.7456 13.0903 12.7456H12.5776ZM14.1111 7.55022C13.8411 6.11027 12.3964 5.21004 10.9848 5.60215L6.03471 6.97717C5.66715 7.07927 5.38971 7.38158 5.31945 7.75652L5.09548 8.95191C5.04235 9.23544 5.2566 9.61617 5.65293 9.78052C5.96222 9.90877 6.31198 10.0858 6.67791 10.3298C8.9648 11.8544 9.80648 14.0256 10.3539 15.4377L10.362 15.4585C10.5515 15.9474 10.6907 16.3017 10.8336 16.5399C10.9027 16.6551 10.9544 16.7105 10.9852 16.7347C10.9933 16.7411 10.9986 16.7442 11.0012 16.7456C11.1431 16.7453 11.2464 16.6914 11.3495 16.542C11.4685 16.3694 11.5658 16.0905 11.6277 15.7121C11.7504 14.9615 11.7048 14.015 11.6332 13.2951C11.6048 13.0097 11.5731 12.767 11.5486 12.5963C11.5364 12.5109 11.5259 12.4438 11.5187 12.3984L11.5103 12.3473L11.5082 12.3349L11.5077 12.3322C11.4823 12.1867 11.5224 12.037 11.6173 11.924C11.6688 11.8627 11.7336 11.8154 11.8056 11.785C11.8665 11.7593 11.9325 11.7456 12.0002 11.7456H13.0903C14.0295 11.7456 14.7377 10.8923 14.5646 9.96918L14.1111 7.55022Z" fill="#424242"></path>
                  </svg>
                </div>
              </div>
            </div>
          </div>
        </div>
        <script>
          function copyText() {
            // Get the text field 
            var copyText = document.getElementById("summary_final");
            // Select the text field 
            navigator.clipboard.writeText(copyText.innerHTML);
          }
    
          function showResult() {
            var chevron = document.getElementById('chevron');
            var content = document.getElementById('Summary_text');
            // Toggle the content display 
            if (content.style.display === 'none' || content.style.display === '') {
              content.style.display = 'block';
              const id = new URL(window.location.href).searchParams.get("id");
              shell.ajaxSafePost({
                type: "POST",
                url: "/_api/summarization/data/v1.0/incidents(" + id + ")?$select=description,title&$expand=incident_adx_portalcomments($select=description)",
              }).done(function(response) {
                console.log("pass", response);
                document.getElementById('summary_final').innerText = response.Summary;
                document.getElementById('shimmer').style.display = "none";
                content.style.display = "block";
                chevron.classList.add('collapsed'); // Log the response when the request is successful 
              }).fail(function() {
                console.log("fail"); // Log an error message when the request fails 
              });
            } else {
              content.style.display = 'none';
              chevron.classList.remove('collapsed'); // Remove rotate class when collapsed      
            }
          }
        </script>
        </div>
      </body>
    </html>
    ```

1. Save the file.
1. Select **Preview** to open the site.

## Step 3 - Test the summarization

1. Select the **My support** tab.
1. Create a new case and add a case description.
1. Add comments.
1. To view the case summary, select the down arrow in the Copilot summary section.
1. Repeat these steps for other case records.

    :::image type="content" source="media/add-copilot-summarization-to-case-page/ai-summarization.png" alt-text="Screenshot of AI summarization on the case page.":::

## Related information

- [Data summarization API (preview)](data-summarization-api.md)
- [FAQ for data summarization API](..\faqs-data-summarization.md)
