---
title: "Générer un schéma XDR en ligne | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XDR schemas [SQL Server]
- inline XDR schema generation [SQL Server]
- XMLDATA option
- FOR XML clause, inline XDR schema generation
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
caps.latest.revision: "32"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0df450f4662cfc9ac11820daaa47c0c0c03a3b31
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="generate-an-inline-xdr-schema"></a>Générer un schéma XDR en ligne
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] La directive **XMLDATA** de FOR XML retourne un schéma XDR inclus avec le résultat de la requête. Toutefois, le schéma XDR ne prend pas en charge tous les nouveaux types de données et autres améliorations introduites dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures. Au lieu de cela, vous pouvez demander un schéma XSD en ligne à l’aide de [la directive XMLSCHEMA](../../relational-databases/xml/generate-an-inline-xsd-schema.md).  
  
> [!IMPORTANT]  
>  La directive XMLDATA de l'option FOR XML est déconseillée. Utilisez la génération XSD en mode RAW et AUTO. Il n'y a aucun remplacement pour la directive XMLDATA en mode EXPLICIT. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Notez également les éléments suivants concernant la prise en charge de schéma XDR en ligne :  
  
-   Si le résultat de la requête FOR XML contient des colonnes de type **xml** et que vous demandez un schéma XDR en ligne, une erreur est retournée. XDR en ligne ne prend pas en charge ces types.  
  
-   Les types **(n)varchar(max)** et **(n)varbinary(max)** seront mappés respectivement à **(n)varchar(n)** et **varbinary(n)**.  
  
-   Quand le mode de compatibilité a la valeur 90 ou une valeur supérieure, les valeurs **timestamp** sont considérées comme des données **varbinary(8)** , sont traitées comme des données binaires et sont retournées dans le résultat de la manière suivante :  
  
    -   L’encodage en base 64 est utilisé quand **binary base64** est spécifié.  
  
    -   L’encodage des URL est utilisé en mode AUTO quand **binary base64** n’est pas spécifié.  
  
  
