---
title: Types de données de collation et d’intégration CLR (fr) Microsoft Docs
description: Dans l’intégration SQL Server CLR, les API chaîne .NET Framework utilisent la propriété CompareInfo de CultureInfo du fil actuel pour effectuer des comparaisons de chaînes.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
ms.openlocfilehash: 46e4d450db90e4bfc93187a48ca8adae472036c6
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488486"
---
# <a name="collation-and-clr-integration-data-types"></a>Classement et types de données de l'intégration du CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Dans [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]le , l’objet **CompareInfo** gère les collations. Les [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] interfaces de programmation d’applications de chaîne (API) utilisent la propriété **CompareInfo** associée à l’objet **CultureInfo** du fil actuel pour effectuer des comparaisons de chaînes. Le paramètre par défaut de l’objet **CultureInfo** est basé sur le [!INCLUDE[msCoName](../../includes/msconame-md.md)] paramètre local Windows pour l’ordinateur sur lequel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. Cela détermine la sémantique de comparaison par défaut, si aucune **CultureInfo** explicite n’est spécifiée, pour les comparaisons des valeurs **System.String.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ne modifie pas explicitement la propriété **CompareInfo** à la base de données ou à la collation du serveur. Si nécessaire, les utilisateurs doivent définir la propriété **CompareInfo** appropriée dans leurs routines.  
  
## <a name="parameter-collation"></a>Paramètre Collation  
 Lorsque vous créez une routine de temps d’exécution de langue commune (CLR), et un paramètre d’une méthode CLR liée à la routine est de type **SQLString**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée une instance du paramètre avec la collation par défaut de la base de données contenant la routine d’appel. Si un paramètre n’est pas un **SqlType** (par exemple, **String** plutôt que **SQLString),** les informations de collation de la base de données ne sont pas associées au paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
