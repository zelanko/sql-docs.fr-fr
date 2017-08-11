---
title: "Exportation vers un fichier Image (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020d8ea2-de07-4212-a2bb-2ed0df2c8db8
caps.latest.revision: 12
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: bf6d4979db2a3b68c34b05fa96f81b47d8034a0b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="exporting-to-an-image-file-report-builder-and-ssrs"></a>Exportation vers un fichier image (Générateur de rapports et SSRS)
  L’extension de rendu de type image effectue le rendu d’un rapport paginé dans un fichier bitmap ou un métafichier. Par défaut, l'extension de rendu de type image génère un fichier TIFF du rapport, qui peut être présenté dans plusieurs pages. Lorsque le client reçoit l'image, il peut l'afficher dans une visionneuse d'images et l'imprimer. Cette rubrique fournit des informations spécifiques au rendu de l'image et décrit les exceptions aux règles de rendu.  
  
 L'extension de rendu de type image peut générer des fichiers dans l'un des formats pris en charge par [!INCLUDE[ndptecgdiplus](../../includes/ndptecgdiplus-md.md)]: BMP, EMF, EMFPlus, GIF, JPEG, PNG et TIFF. Pour le format TIFF, le nom de fichier du flux principal est *ReportName*.tif. Pour tous les autres formats dont le rendu s’effectue sur la base d’une page par fichier, le nom de fichier est *ReportName_Page.ext* . *ext* est l'extension de fichier pour le format choisi. Pour produire un fichier dans un autre format pris en charge par Image, spécifiez l’une des chaînes répertoriées ci-dessus dans le paramètre **OutputFormatDeviceInfo** .  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="SupportedImageFormats"></a> Formats d'image pris en charge  
 Le tableau suivant indique l'extension de fichier et MimeType pour chaque format du convertisseur d'image.  
  
|**Type**|**Extension**|**MIMEType**|  
|--------------|-------------------|------------------|  
|BMP|BMP|image/bmp|  
|GIF|GIF|image/gif|  
|JPEG|JPEG|image/jpeg|  
|PNG|PNG|image/png|  
|TIFF|tif|image/tiff|  
|EMF|EMF|image/emf|  
|EMFPlus|EMF|image/emf|  
  
  
##  <a name="RenderingMultiplePages"></a> Rendu de plusieurs pages  
 TIFF est le seul format qui prend en charge les documents de plusieurs pages dans un unique fichier. D'autres formats, tels que JPG ou PNG, produisent une page à la fois et requièrent un appel séparé à l'extension de rendu pour chaque page.  
  
  
##  <a name="Interactivity"></a> Interactivité  
 L'interactivité n'est pas prise en charge par les formats Image générés par ce convertisseur. Les éléments interactifs suivants ne sont pas rendus :  
  
-   Liens hypertexte  
  
-   Afficher ou masquer  
  
-   Explorateur de documents  
  
-   Liens d'extraction ou interactifs  
  
-   Tri d'utilisateur final  
  
-   En-têtes fixes  
  
-   Signets  
  
  
##  <a name="DeviceInfo"></a> Paramètres d'informations de périphérique  
 Vous pouvez modifier certains paramètres par défaut pour ce convertisseur en modifiant les paramètres d'informations de périphérique. Pour plus d'informations, consultez [Image Device Information Settings](../../reporting-services/image-device-information-settings.md).  
  
  
## <a name="see-also"></a>Voir aussi  
 [Pagination dans Reporting Services &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Comportements de rendu &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Fonctionnalité interactive des différentes Extensions &#40; de rendu de rapport Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-builder/interactive-functionality-different-report-rendering-extensions.md)   
 [Rendu des éléments de rapport &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [Tables, Matrices et listes &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
