---
title: Types de données d’intégration du classement et du CLR | Microsoft Docs
description: Dans SQL Server l’intégration du CLR, les API de chaîne .NET Framework utilisent la propriété CompareInfo de CultureInfo du thread actuel pour effectuer des comparaisons de chaînes.
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
ms.openlocfilehash: e5333da328c36ed184b3e8acbbbd8671bc0b4971
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765343"
---
# <a name="collation-and-clr-integration-data-types"></a>Classement et types de données de l'intégration du CLR
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Dans [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , l’objet **CompareInfo** gère les classements. Les [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] interfaces de programmation d’application (API) de chaîne utilisent la propriété **CompareInfo** associée à l’objet **CultureInfo** du thread actuel pour effectuer des comparaisons de chaînes. Le paramètre par défaut de l’objet **CultureInfo** est basé sur les paramètres [!INCLUDE[msCoName](../../includes/msconame-md.md)] régionaux Windows de l’ordinateur sur lequel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute. Cela détermine la sémantique de comparaison par défaut, si aucun **CultureInfo** explicite n’est spécifié, pour les comparaisons de valeurs **System. String** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ne change pas explicitement la propriété **CompareInfo** en classement de base de données ou de serveur. Si nécessaire, les utilisateurs doivent définir la propriété **CompareInfo** appropriée dans leurs routines.  
  
## <a name="parameter-collation"></a>Paramètre Collation  
 Lorsque vous créez une routine de common language runtime (CLR) et qu’un paramètre d’une méthode CLR liée à la routine est de type **SqlString**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée une instance du paramètre avec le classement par défaut de la base de données qui contient la routine d’appel. Si un paramètre n’est pas un **SQLType** (par exemple, **String** plutôt que **SqlString**), les informations de classement de la base de données ne sont pas associées au paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
