---
title: Mots réservés (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 2aaee670cd89e957a6ad4700963606ffe0d4ef4f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221665"
---
# <a name="reserved-words-master-data-services"></a>Mots réservés (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], lorsque vous créez des objets de modèle ou des membres, certains mots ne peuvent pas être utilisés. Ces mots peuvent provoquer des erreurs.  
  
> [!NOTE]  
>  Vous devez également limiter votre utilisation des caractères spéciaux (symboles, césure, etc.).  
  
-   [Modèles](#models)  
  
-   [Entités](#entities)  
  
-   [Hiérarchies explicites](#exhierarchies)  
  
-   [Attributs](#attributes)  
  
-   [Membres](#members)  
  
##  <a name="models"></a> Modèles  
 Si vous créez un modèle avec le nom de la valeur **nom**, ne sélectionnez pas **créer une entité portant le même nom que le modèle** car **nom** ne peut pas être utilisé pour le nom d’une entité.  
  
##  <a name="entities"></a> Entités  
 Pour les noms d'entité, vous ne pouvez pas utiliser **Name** ou **Code**.  
  
##  <a name="exhierarchies"></a> Hiérarchies explicites  
 Pour les noms de hiérarchies explicites, vous ne pouvez pas utiliser **Name** ou **Code**.  
  
##  <a name="attributes"></a> Attributs  
  
-   **ID**  
  
-   **Code**  
  
-   **Nom**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a> Membres  
 Pour les membres, vous ne pouvez pas utiliser **MDMMemberStatus** ou **racine** pour le **Code** valeur d’attribut.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de Master Data Services](master-data-services-overview-mds.md)  
  
  
