---
title: Générer un schéma XDR en ligne | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XDR schemas [SQL Server]
- inline XDR schema generation [SQL Server]
- XMLDATA option
- FOR XML clause, inline XDR schema generation
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
caps.latest.revision: 31
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 00ef9ba22e2923700e75cd7c38bc7e68a716da5c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050999"
---
# <a name="generate-an-inline-xdr-schema"></a>Générer un schéma XDR en ligne
  La directive **XMLDATA** de FOR XML retourne un schéma XDR en ligne avec le résultat de la requête. Toutefois, le schéma XDR ne prend pas en charge tous les nouveaux types de données et autres améliorations introduites dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures. Au lieu de cela, vous pouvez demander un schéma XSD en ligne à l’aide de [la directive XMLSCHEMA](generate-an-inline-xsd-schema.md).  
  
> [!IMPORTANT]  
>  La directive XMLDATA de l'option FOR XML est déconseillée. Utilisez la génération XSD en mode RAW et AUTO. Il n'y a aucun remplacement pour la directive XMLDATA en mode EXPLICIT. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Notez également les éléments suivants concernant la prise en charge de schéma XDR en ligne :  
  
-   Si le résultat de la requête FOR XML contient des colonnes de type **xml** et que vous demandez un schéma XDR en ligne, une erreur est retournée. XDR en ligne ne prend pas en charge ces types.  
  
-   Les types **(n)varchar(max)** et **(n)varbinary(max)** seront mappés respectivement à **(n)varchar(n)** et **varbinary(n)**.  
  
-   Quand le mode de compatibilité a la valeur 90 ou une valeur supérieure, les valeurs **timestamp** sont considérées comme des données **varbinary(8)** , sont traitées comme des données binaires et sont retournées dans le résultat de la manière suivante :  
  
    -   L’encodage en base 64 est utilisé quand **binary base64** est spécifié.  
  
    -   L’encodage des URL est utilisé en mode AUTO quand **binary base64** n’est pas spécifié.  
  
  