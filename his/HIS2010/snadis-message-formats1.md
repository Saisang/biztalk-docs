---
title: "SNADIS Message Formats1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5c9eb5f-e1c0-4441-8e41-92022bc21734
caps.latest.revision: 3
---
# SNADIS Message Formats
This section describes the SNA Device Interface Specification interface in terms of message formats. These are presented in a language-independent notation that is described below.  
  
 The messages used between the node and the SNALinks are shown in the following table.  
  
|Message type|Direction|LPI connection|  
|------------------|---------------|--------------------|  
|**Open(LINK)Request**|NODE ------> DLC|LINK|  
|**Close(LINK)Request**|NODE ------> DLC|LINK|  
|**Send-XID**|NODE ------> DLC|LINK|  
|**Open(STATION) Request**|NODE ------> DLC|STATION|  
|**Close(STATION) Request**|NODE ------> DLC|STATION|  
|**Open(LINK) Response**|NODE <------ DLC|LINK|  
|**Close(LINK) Response**|NODE <------ DLC|LINK|  
|**Request-Open-Station**|NODE <------ DLC|LINK|  
|**Open(STATION) Response**|NODE <------ DLC|STATION|  
|**Close(STATION) Response**|NODE <------ DLC|STATION|  
|**Station-Contacted**|NODE <------ DLC|STATION|  
|**Outage**|NODE <------ DLC|LINK/STATION|  
|**DLC-Data**|NODE \<-----> DLC|STATION|  
|**Status-Resource**|NODE \<-----> DLC|STATION|  
  
 Details of the message format notation and key assumptions about the contents of the message formats are as follows:  
  
-   "Reserved" indicates that the field must be set to zero (for a numeric field) or all nulls (for names) by the sender of the message.  
  
-   "Undefined" indicates that the value of the field is indeterminate. The field is not set by the sender and should not be examined by the receiver of the message.  
  
-   Fields that occupy two bytes — the **srci** field in all messages, and fields such as **opresid** in [Open(LINK) Request](../HIS2010/open-link-request2.md) — are represented with the arithmetically most significant byte in the lowest byte address, irrespective of the normal byte order used by the processor on which the software executes. That is, the 2-byte value 0x1234 has the byte 0x12 in the lowest byte address. The exception to this is the **startd** and **endd** fields in all elements, which are always stored in the processor's normal byte order.  
  
-   Messages are composed of buffers, consisting of a buffer header and zero or more buffer elements. For more information on buffer formats, see [Messages](../HIS2010/messages-snadis-2.md).  
  
-   The **startd** field in each element gives the offset of the first byte of data in the element after the **trpad** field. Its value will either be 1 (data starts in the byte after the **trpad** field), 10 (nine bytes of padding are included between the **trpad** field and the start of the data), or 13 (12 bytes of padding are included between the **trpad** field and the start of the data). Any extra bytes are used by the local node for additional header information. This avoids having to copy data into a new buffer when adding this information.  
  
-   Because **startd** indicates the index into **dataru** starting from 1, not 0, the first byte of valid data will always be at **dataru[startd–1]**.  
  
-   All fields within **dataru** are of type unsigned character (UCHAR), except where the notes indicate otherwise.  
  
## In This Section  
  
-   [Open(LINK)](../HIS2010/open-link-2.md)  
  
-   [Open(LINK) Request](../HIS2010/open-link-request2.md)  
  
-   [Open(LINK) Response](../HIS2010/open-link-response1.md)  
  
-   [Close(LINK)](../HIS2010/close-link-2.md)  
  
-   [Close(LINK) Request](../HIS2010/close-link-request2.md)  
  
-   [Close(LINK) Response](../HIS2010/close-link-response1.md)  
  
-   [Open(STATION)](../HIS2010/open-station-2.md)  
  
-   [Open(STATION) Request](../HIS2010/open-station-request1.md)  
  
-   [Open(STATION) OK Response](../HIS2010/open-station-oresponse2.md)  
  
-   [Open(STATION) Error Response](../HIS2010/open-station-error-response2.md)  
  
-   [Close(STATION)](../HIS2010/close-station-2.md)  
  
-   [Close(STATION) Request](../HIS2010/close-station-request1.md)  
  
-   [Close(STATION) Response](../HIS2010/close-station-response2.md)  
  
-   [Request-Open-Station](../HIS2010/request-open-station1.md)  
  
-   [Station-Contacted](../HIS2010/station-contacted2.md)  
  
-   [Outage](../HIS2010/outage1.md)  
  
-   [Status-Resource](../HIS2010/status-resource-snadis-2.md)  
  
-   [Send-XID](../HIS2010/send-xid2.md)  
  
-   [DLC-Data](../HIS2010/dlc-data2.md)