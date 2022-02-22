---
author: David Wasserbauer
---

# Icon 
Icon is type of **WebResource**. We use them mainly in **SiteMap** to improve **user experience**. 

![Site Map Icons](/.attachments/SiteMap.png)

## **Conventions**

### **Code placement**
There are **2 files**. One with **.svg** file type and second with **.svg.data.xml** file type. 
Both of them have to be stored in **same folder**:

…\CDS\WebResources\

### **.svg file** 
___
.svg file contains definition of the Icon. There are plenty of icons in TALXIS. 

In case you need to add a new one you are free to use Office UI Fabric Icon Generator.
We have this handy tool pinned in tabs in INT006 - TALXIS Apps team (General channel).

Link: [Office UI Fabric Icon Generator](https://teams.microsoft.com/l/entity/a6b63365-31a4-4f43-92ec-710b71557af9/_djb2_msteams_prefix_1846344613?context=%7B%22subEntityId%22%3Anull%2C%22channelId%22%3A%2219%3A65f6197f7c8f4840b5ee62407f277173%40thread.skype%22%7D&groupId=e5ff28e3-d44d-4faf-92fb-88c0409bf683&tenantId=67266d43-8de7-494d-9ed8-3d1bd3b3a764) 



### **.svg.data.xml file**
___

#### **Icon Id**
Make sure that GUID in `<WebResourceId>` is unique. 

**Example:**
```xml
<WebResourceId>{3d4967df-91a3-4f86-ba43-f7cc78ad97bd}</WebResourceId>
```

#### **Name Parameter**
This parameter references the definition of the icon so it has to match with .svg file name. 

**Example:** 
```xml
<Name>talxis_taskicon.svg</Name>
```

#### **FileName Parameter**
This parameter should reference to the defition of the Icon. Hovewer we find out that mistakes in this parameter do not cause failure of the icon. 

On the other hand please be responsible and use this format: 
>/WebResources/{Icon File name}{svg}{WerResourceID in UpperCase}


**Example:** 
```xml
<FileName>/WebResources/talxis_taskiconsvg3D4967DF-91A3-4F86-BA43-F7CC78AD97BD</FileName>
```
___

## Presentation/Model
Icons are somehow part of presentation layer but it will be better to put their definitions in model layer. In TALXIS you will often find icons in presentation layer but we try to put them in model nowadays. 

You can use an icon as **main icon for an entity**. 
Since entity definition is placed in model layer you have to put your icon in model layer too. 

![Icon Placement](/.attachments/IconPlacement.png)

You can see that in this case one icon is placed in MODEL (model layer) and one in APPS (presentation layer).

### **Presentation Icons**
To set **specific icon** for **SubArea of a [AppModule](https://docs.talxis.com/en/developer-guide/applications/solution-components/appmodule/#sitemap)** you have to add `Icon` and `VectorIcon` parameter which is referencing the icon.

**Example:**
```xml
<SubArea Id="HugeUnitsSubArea" ResourceId="SitemapDesigner.NewSubArea" VectorIcon="/WebResources/talxis_producticon.svg" Icon="/WebResources/talxis_producticon.svg" Url="/main.aspx?etn=talxis_buildingunit&amp;pagetype=entitylist&amp;viewid={34bffe6b-9e30-eb11-a813-0022487f4737}" Client="All,Outlook,OutlookLaptopClient,OutlookWorkstationClient,Web" AvailableOffline="true" PassParams="false" Sku="All,OnPremise,Live,SPLA">
	<Titles>
		<Title LCID="1033" Title="Huge Units" />
	</Titles>
</SubArea>
```

### **Model Icons**
The icon with file name **talxis_contract.svg** (picture above) is referenced in **Entity.xml** of **talxis_contract** entity:


```xml
<IconMediumName>talxis_contract.svg</IconMediumName>
<IconSmallName>talxis_contract.svg</IconSmallName>
<IconVectorName>talxis_contract.svg</IconVectorName>
```

Thanks to the reference in **Entity.xml** this icon will be used by default in **SiteMap**(Just in case you reference the entity. If you specify URL you need to do go same as with presentation icons). You do not have to reference it in **SiteMap** as you have to do with **icons in presentation layer**. 

However you are able to set only **one icon** for the **entity**. To change the icon you have to use **icons in presentation layer**.
