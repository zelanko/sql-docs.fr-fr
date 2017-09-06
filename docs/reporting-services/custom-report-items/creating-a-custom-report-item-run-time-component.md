---
title: "Création d’un composant d’exécution de rapport personnalisé élément | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, creating
ms.assetid: b3e15a4a-98f8-4dbb-b847-bbcb20327051
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: c8da0d4ac6024281315dc2e8b0b398904c8a1e6c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/14/2017

---
# <a name="creating-a-custom-report-item-run-time-component"></a>Création d'un composant d'exécution d'élément de rapport personnalisé
  Le composant d’exécution élément rapport personnalisé est implémenté comme un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] composant à l’aide de n’importe quel langage conforme CLS et est appelé par le processeur de rapports au moment de l’exécution. Les propriétés du composant d'exécution sont définies dans l'environnement de conception en modifiant le composant de conception d'élément de rapport personnalisé y correspondant.  
  
 Pour voir un exemple d’un élément de rapport personnalisé totalement implémenté, [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="definition-and-instance-objects"></a>Objets d'instance et de définition  
 Avant d’implémenter un élément de rapport personnalisé, il est important de comprendre la différence entre *des objets de définition* et *objets d’instance*. Les objets de définition fournissent la représentation RDL de l'élément de rapport personnalisé alors que les objets d'instance sont les versions évaluées des objets de définition. Il n'existe qu'un seul objet de définition pour chaque élément du rapport. Lorsque vous accédez aux propriétés d'un objet de définition qui contient des expressions, vous obtenez une chaîne d'expression non-évaluée. Les objets d'instance contiennent les versions évaluées des objets de définition et peuvent avoir une relation un-à-plusieurs avec l'objet de définition d'un élément. Par exemple, lorsque la région de données <xref:Microsoft.ReportingServices.OnDemandReportRendering.Tablix> d'un rapport contient un composant <xref:Microsoft.ReportingServices.OnDemandReportRendering.CustomReportItem> dans l'une de ses lignes de détails, un seul objet de définition y correspond. En revanche, plusieurs objets d'instance sont spécifiés, un pour chaque ligne que comporte la région de données.  
  
## <a name="implementing-the-icustomreportitem-interface"></a>Implémentation de l'interface ICustomReportItem  
 Pour créer un **CustomReportItem** composant d’exécution vous devez implémenter la <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> interface qui est définie dans le fichier Microsoft.ReportingServices.ProcessingCore.dll :  
  
```csharp  
namespace Microsoft.ReportingServices.OnDemandReportRendering  
{  
    public interface ICustomReportItem  
    {  
        void GenerateReportItemDefinition(CustomReportItem customReportItem);  
void EvaluateReportItemInstance(CustomReportItem customReportItem);  
    }  
}  
```  
  
 Une fois l'interface <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> implémentée, deux stubs de méthode sont générés : <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> et <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A>. La méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> est appelée en premier et est utilisée pour définir des propriétés de définition et créer l'objet <xref:Microsoft.ReportingServices.OnDemandReportRendering.Image> qui contiendra à la fois les propriétés de définition et d'instance utilisées pour le rendu de l'élément. La méthode <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> est appelée une fois les objets de définition évalués. Elle fournit en outre les objets d'instance utilisés pour le rendu de l'élément.  
  
 L'exemple suivant illustre l'implémentation d'un élément de rapport personnalisé qui restitue le nom du contrôle sous la forme d'une image.  
  
```csharp  
namespace Microsoft.Samples.ReportingServices  
{  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.Specialized;  
    using System.Drawing.Imaging;  
    using System.IO;  
    using System.Text;  
    using Microsoft.ReportingServices.OnDemandReportRendering;  
  
    public class PolygonsCustomReportItem : ICustomReportItem  
    {  
        #region ICustomReportItem Members  
  
        public void GenerateReportItemDefinition(CustomReportItem cri)  
        {  
            // Create the Image object that will be   
            // used to render the custom report item  
            cri.CreateCriImageDefinition();  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
        }  
  
        public void EvaluateReportItemInstance(CustomReportItem cri)  
        {  
            // Get the Image definition  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
  
            // Create the image for the custom report item  
            polygonImage.ImageInstance.ImageData = DrawImage(cri);  
        }  
  
        #endregion  
  
        /// <summary>  
        /// Creates an image of the CustomReportItem's name  
        /// </summary>  
        private byte[] DrawImage(CustomReportItem customReportItem)  
        {  
            int width = 1;          // pixels  
            int height = 1;         // pixels  
            int resolution = 75;    // dpi  
  
            System.Drawing.Bitmap bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            System.Drawing.Graphics graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Get the Font for the Text  
            System.Drawing.Font font = new System.Drawing.Font(System.Drawing.FontFamily.GenericMonospace,  
                12, System.Drawing.FontStyle.Regular);  
  
            // Get the Brush for drawing the Text  
            System.Drawing.Brush brush = new System.Drawing.SolidBrush(System.Drawing.Color.LightGreen);  
  
            // Get the measurements for the image  
            System.Drawing.SizeF maxStringSize = graphics.MeasureString(customReportItem.Name, font);  
            width = (int)(maxStringSize.Width + 2 * font.GetHeight(resolution));  
            height = (int)(maxStringSize.Height + 2 * font.GetHeight(resolution));  
  
            bitmap.Dispose();  
            bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            graphics.Dispose();  
            graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Draw the text  
            graphics.DrawString(customReportItem.Name, font, brush, font.GetHeight(resolution),   
                font.GetHeight(resolution));  
  
            // Create the byte array of the image data  
            MemoryStream memoryStream = new MemoryStream();  
            bitmap.Save(memoryStream, ImageFormat.Bmp);  
            memoryStream.Position = 0;  
            byte[] imageData = new byte[memoryStream.Length];  
            memoryStream.Read(imageData, 0, imageData.Length);  
  
            return imageData;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture d’élément de rapport personnalisé](../../reporting-services/custom-report-items/custom-report-item-architecture.md)   
 [Création d’un composant au moment du Design d’élément rapport personnalisé](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Bibliothèques de classes élément de rapport personnalisé](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)   
 [Comment : déployer un élément de rapport personnalisé](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
