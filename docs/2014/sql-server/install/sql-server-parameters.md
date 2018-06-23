---
title: Paramètres de SQL Server | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Database Engine analysis [Upgrade Advisor]
- SQL Server Upgrade Advisor, Database Engine
- Upgrade Advisor [SQL Server], Database Engine
- analyzing system [Upgrade Advisor], Database Engine
ms.assetid: 44a18bfe-e593-47a5-995f-382c01d3f618
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1a0c7676aa40d78967f6ff97a6ac91cdef4f0844
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038725"
---
# <a name="sql-server-parameters"></a>Paramètres du serveur SQL Server
  Sur cette page, définir les paramètres utilisés par l’analyseur pour [!INCLUDE[ssDE](../../includes/ssde-md.md)] analysis. ous pouvez analyser une, plusieurs ou toutes les bases de données, des fichiers de trace créés à l'aide de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et des fichiers de commandes SQL.  
  
> [!NOTE]  
>  Certains problèmes de mise à niveau ne peuvent être détectés que si vous faites analyser des fichiers de trace ou des fichiers de commandes SQL.  
  
## <a name="options"></a>Options  
 **Base de données à analyser**  
 Pour analyser toutes les bases de données, activez la **toutes les bases de données** case à cocher. Pour analyser une sélection de bases de données, activez la case à cocher située en regard de chaque base de données à inclure dans l'analyse.  
  
 **Analyser les fichiers de trace**  
 Activez cette case à cocher pour analyser les fichiers de trace du système de fichiers.  
  
 **Chemin d’accès aux fichiers de trace**  
 Vous pouvez analyser un ou plusieurs fichiers. Vous pouvez accéder à un emplacement et sélectionner plusieurs fichiers, ou vous pouvez fournir plusieurs noms de fichiers. Utilisez le chemin d'accès complet à chaque fichier, incluez le nom de fichier et séparez les entrées à l'aide de la barre verticale (|).  
  
 Si vous activez **analyser les fichiers de trace**, **suivant** est désactivé jusqu'à ce que vous entrez un nom de chemin d’accès et un nom de fichier.  
  
 **Analyser les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les fichiers du lot**  
 Activez cette case à cocher pour analyser les fichiers de commandes [!INCLUDE[tsql](../../includes/tsql-md.md)] du système de fichiers.  
  
 **Chemin d’accès au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les fichiers du lot**  
 Vous pouvez analyser un ou plusieurs fichiers de commandes. Vous pouvez accéder à un emplacement et sélectionner plusieurs fichiers, ou vous pouvez taper plusieurs noms de fichiers. Utilisez le chemin d'accès complet à chaque fichier, incluez le nom de fichier et séparez les entrées à l'aide de la barre verticale (|).  
  
 Si vous activez **SQL d’analyser les fichiers de commandes**, le **suivant** bouton est désactivé jusqu'à ce que vous entrez un nom de chemin d’accès et un nom de fichier.  
  
 **Délimiteur de lot SQL**  
 Texte utilisé pour séparer des lots d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. La valeur par défaut est **accédez**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation avec le Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Référence de l’Interface utilisateur Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  