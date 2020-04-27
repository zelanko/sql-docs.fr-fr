---
title: Les constantes de grande taille sont typées en tant que types de valeur élevée dans les modes de compatibilité 90 ou ultérieur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- binary constants
- CHARINDEX function
- constants
- character string constants
- PATINDEX function
ms.assetid: 6e309fa0-5fb9-45a1-9739-f13fae525bfe
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c7aded5577e28d94f42e108e46bb8a9c3cd6020
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094092"
---
# <a name="large-constants-are-typed-as-large-value-types-in-90-or-later-compatibility-modes"></a>Les constantes importantes sont tapées en tant que types à valeur élevée en mode de compatibilité 90 ou ultérieur
  Le Conseiller de mise à niveau a détecté la présence de constantes importantes. Les constantes de chaîne de caractères et les constantes binaires dont la taille dépasse 8 000 octets sont traitées comme des types de données d'objet volumineuses dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, les constantes caractère, Unicode et binaires importantes sont tapées en tant que types à valeurs élevées.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Lorsque des fonctions de chaîne, telles que CHARINDEX et PATINDEX, sont utilisées avec des constantes de chaîne ou binaires dont la taille dépasse 8 000octets, [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] retourne le numéro d'erreur 8116 et [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure retourne le numéro d'erreur 8152.  
  
 Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], les fonctions de chaîne retournent l'erreur 8116 lorsqu'elles sont utilisées avec les types de données `text`, `ntext` et `image`.  
  
 Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, les constantes importantes sont traitées comme des types de données `varchar(max)`, `nvarchar(max)` et `varbinary(max)`. Ces types de données sont compatibles avec les fonctions de chaîne.  
  
 Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, les fonctions de chaîne, telles que CHARINDEX et PATINDEX, supposent que la taille de la chaîne qui contient la séquence de caractères à rechercher est inférieure à 8 000 octets. C'est pour cette raison que l'erreur 8152 est générée pour CHARINDEX et PATINDEX.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
