---
title: Autres Annotations (SQLXML 4.0) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9f379a046b73dbd073c7e0f01b5c41be7589964d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052155"
---
# <a name="other-annotations-sqlxml-40"></a>Autres annotations (SQLXML 4.0)
  Outre les annotations présentées dans les rubriques précédentes de cette section, le chargement en masse XML interprète les annotations suivantes, comme suit :  
  
 `sql:id-prefix`  
 Si conformément au schéma, des préfixes sont ajoutés aux données XML, le chargement en masse XML supprime ces préfixes avant d'envoyer les données à Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 `sql:use-cdata`  
 Le chargement en masse XML lit le texte qui est stocké dans les sections CDATA et l'envoie à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 `sql:url-encode`  
 Le chargement en masse XML ne prend pas en charge cette annotation. Par exemple, vous ne pouvez pas spécifier une URL dans l'entrée de données XML et vous attendre à ce que le chargement en masse XML lise les données à cet emplacement et les stocke dans la base de données.  
  
 `sql:is-mapping-schema`  
 Le chargement en masse XML ne prend pas en charge cette annotation, ni `sql:id`.  
  
> [!NOTE]  
>  Le chargement en masse XML ne prend pas en charge les schémas de mappage insérés.  
  
 `sql:key-fields`  
 Le chargement en masse XML ignore toujours cette annotation.  
  
## <a name="see-also"></a>Voir aussi  
 [Interprétation d’annotation &#40;SQLXML 4.0&#41;](annotation-interpretation-sqlxml-4-0.md)  
  
  