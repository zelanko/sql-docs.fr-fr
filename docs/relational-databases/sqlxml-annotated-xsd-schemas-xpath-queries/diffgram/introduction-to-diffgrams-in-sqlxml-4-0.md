---
title: Introduction aux DiffGrams dans SQLXML 4.0
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotations [SQLXML]
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: 1902d67f-baf3-46e6-a36c-b24b5ba6f8ea
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3994a9d0bc863367edf5b1844772b94a63f19d4d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75257251"
---
# <a name="introduction-to-diffgrams-in-sqlxml-40"></a>Introduction aux DiffGrams dans SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Cette rubrique fournit une brève introduction aux DiffGrams.  
  
## <a name="diffgram-format"></a>Format DiffGram  
 Voici le format DiffGram général :  
  
```  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
   <DataInstance>  
      ...  
   </DataInstance>  
   [<diffgr:before>  
        ...  
   </diffgr:before>]  
  
   [<diffgr:errors>  
        ...  
   </diffgr:errors>]  
</diffgr:diffgram>  
```  
  
 Le format DiffGram est constitué des blocs suivants :  
  
 **\<DataInstance>**  
 Le nom de cet élément, **DataInstance**, est utilisé à des fins d’explication dans cette documentation. Par exemple, si le DiffGram a été généré à partir d’un DataSet dans le .NET Framework, la valeur de la propriété **Name** du DataSet est utilisée comme nom de cet élément. Ce bloc contient toutes les données pertinentes après la modification, y compris éventuellement les données qui n'ont pas été modifiées. La logique de traitement DiffGram ignore les éléments de ce bloc pour lesquels l’attribut **diffgr : hasChanges** n’est pas spécifié.  
  
 **\<diffgr : avant>**  
 Ce bloc facultatif contient les instances (éléments) de l'enregistrement d'origine qui doivent être mises à jour ou supprimées. Toutes les tables de base de données qui sont modifiées (mises à jour ou supprimées) par le DiffGram doivent apparaître en tant qu’éléments de niveau supérieur dans le ** \<bloc Before>** .  
  
 **\<diffgr : Errors>**  
 Ce bloc facultatif est ignoré par la logique de traitement DiffGram.  
  
## <a name="diffgram-annotations"></a>Annotations DiffGram  
 Ces annotations sont définies dans l’espace de noms DiffGram **« urn : schemas-microsoft-com : XML-DiffGram-01 »**:  
  
 **identifi**  
 Cet attribut est utilisé pour coupler les éléments dans les ** \<blocs Before>** et ** \<DataInstance>** .  
  
 **hasChanges**  
 Pour une opération d’insertion ou de mise à jour, le DiffGram doit spécifier cet attribut avec la valeur **insérée** ou **modifiée**. Si cet attribut n’est pas présent, l’élément correspondant dans la ** \<>DataInstance** est ignoré par la logique de traitement et aucune mise à jour n’est effectuée. Pour obtenir des exemples fonctionnels, consultez [exemples DiffGram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).  
  
 **ID**  
 Cet attribut est utilisé pour spécifier les relations parent-enfant parmi les éléments du DiffGram. Cet attribut apparaît uniquement dans le \<bloc before>. Il est utilisé par SQLXML lors de l'application de mises à jour. La relation parent-enfant est utilisée pour déterminer l'ordre dans lequel les éléments du DiffGram sont traités.  
  
## <a name="understanding-the-diffgram-processing-logic"></a>Fonctionnement de la logique de traitement DiffGram  
 La logique de traitement DiffGram utilise certaines règles pour déterminer si une opération est une opération d'insertion, de mise à jour ou de suppression. Ces règles sont décrites dans le tableau suivant.  
  
|Opération|Description|  
|---------------|-----------------|  
|Insérer|Un DiffGram indique une opération d’insertion lorsqu’un élément apparaît dans le ** \<bloc DataInstance>** , mais pas dans le bloc ** \<Before>** correspondant, et l’attribut **diffgr : hasChanges** est spécifié (**diffgr : hasChanges = inserted**) sur l’élément. Dans ce cas, le DiffGram insère l’instance d’enregistrement spécifiée dans le ** \<bloc DataInstance>** dans la base de données.<br /><br /> Si l’attribut **diffgr : hasChanges** n’est pas spécifié, l’élément est ignoré par la logique de traitement et aucune insertion n’est effectuée. Pour obtenir des exemples fonctionnels, consultez [exemples DiffGram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).|  
|Update|Le DiffGram indique une opération de mise à jour lorsqu’il existe un \<élément dans le bloc Before> pour lequel il existe un élément correspondant dans le ** \<bloc DataInstance>** (autrement dit, les deux éléments ont un attribut **diffgr : ID** avec la même valeur) et l’attribut **diffgr : hasChanges** est spécifié avec la valeur **modifiée** sur l’élément dans le ** \<bloc de>DataInstance** .<br /><br /> Si l’attribut **diffgr : hasChanges** n’est pas spécifié sur l’élément du bloc ** \<DataInstance>** , une erreur est retournée par la logique de traitement. Pour obtenir des exemples fonctionnels, consultez [exemples DiffGram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).<br /><br /> Si **diffgr : ParentId** est spécifié dans le ** \<bloc Before>** , la relation parent-enfant des éléments spécifiés par **ParentId** est utilisée pour déterminer l’ordre dans lequel les enregistrements sont mis à jour.|  
|DELETE|Un DiffGram indique une opération de suppression lorsqu’un élément apparaît dans le ** \<bloc Before>** , mais pas dans le bloc de ** \<>DataInstance** correspondant. Dans ce cas, le DiffGram supprime l’instance d’enregistrement spécifiée dans le ** \<bloc Before>** de la base de données. Pour obtenir des exemples fonctionnels, consultez [exemples DiffGram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).<br /><br /> Si **diffgr : ParentId** est spécifié dans le ** \<bloc Before>** , la relation parent-enfant des éléments spécifiés par **ParentId** est utilisée pour déterminer l’ordre dans lequel les enregistrements sont supprimés.|  
  
> [!NOTE]  
>  Les paramètres ne peuvent pas être passés aux DiffGrams.  
  
  
