---
title: MSSQLSERVER_1105 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 1105 (Database Engine error)
ms.assetid: e7f4ad02-8c7f-4bb9-9781-2c86253f2138
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28cb37ebdca0e3bb0078c591a78ff099ac44c5a7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1105"></a>MSSQLSERVER_1105
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1105|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NO_MORE_SPACE_IN_FG|  
|Texte du message|Impossible d’allouer de l’espace pour l’objet ’%.*ls’%.\*ls dans la base de données ’%.\*ls’, car le groupe de fichiers ’%.\*ls’ est plein. Créez de l'espace disque en supprimant des fichiers qui ne sont pas indispensables, en supprimant des objets dans le groupe de fichiers, en ajoutant des fichiers supplémentaires au groupe de fichiers ou en définissant Autogrowth à ON pour les fichiers existants dans le groupe de fichiers.|  
  
## <a name="explanation"></a>Explication  
Il n'y a pas d'espace disque disponible dans un groupe de fichiers.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Les actions ci-dessous peuvent éventuellement créer de l'espace disponible dans le groupe de fichiers :  
  
-   Activez la croissance automatique.  
  
-   Ajoutez d'autres fichiers au groupe de fichiers.  
  
-   Libérez de l'espace disque en supprimant des index ou des tables qui ne sont plus nécessaires.  
  
-   Pour plus d'informations, consultez la section « Résolution des problèmes d'espace disque insuffisant » dans la documentation en ligne de SQL Server.  
  
> [!NOTE]  
> Si un index se trouve sur plusieurs fichiers, **ALTER INDEX REORGANIZE** peut retourner une erreur 1105 quand l’un des fichiers est plein. Le processus de réorganisation est bloqué quand il tente de déplacer des lignes vers le fichier plein. Pour contourner cette limitation, effectuez une opération **ALTER INDEX REBUILD** au lieu de **ALTER INDEX REORGANIZE** ou augmentez la limite de croissance des fichiers qui sont pleins.  
  
