---
title: Infos express (IntelliSense)
description: Découvrez comment utiliser l’option IntelliSense Rapide pour afficher la déclaration complète de tout identificateur présent dans votre code. Dans SQL Server Management Studio, l’option est disponible dans l’éditeur de Moteur de base de données et l’éditeur de requête XML.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1ade62b8c3a72bbc21f249c4b725047ef96624e4
ms.sourcegitcommit: d855def79af642233cbc3c5909bc7dfe04c4aa23
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87122528"
---
# <a name="quick-info-intellisense"></a>Infos express (IntelliSense)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  L’option [!INCLUDE[msCoName](../../includes/msconame-md.md)] Info express **de** IntelliSense affiche la déclaration complète de tout identificateur présent dans votre code. Lorsque vous déplacez le pointeur de la souris sur un identificateur, sa déclaration apparaît dans une fenêtre indépendante jaune. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **Info express** est disponible dans les éditeurs de requête XML et du moteur de base de données.  
  
## <a name="transact-sql-quick-info"></a>Info express (Transact-SQL)  
 **Info express** affiche deux types d’informations dans l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Quand l’option **Info express** n’est pas en mode débogage, elle affiche la déclaration de l’expression. En revanche, en mode débogage, **Info express** affiche le nom de l’expression et sa valeur actuelle.  
  
 Dans l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , **Info express** n’est disponible que pour les parties de la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] prises en charge par IntelliSense. Par exemple, si vous déplacez le pointeur de la souris sur l’identificateur d’un objet dont le type de données n’est pas pris en charge par IntelliSense, la fenêtre indépendante **Info express** contient un message indiquant que le type de données n’est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe Transact-SQL prise en charge par IntelliSense](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md)  
  
  
