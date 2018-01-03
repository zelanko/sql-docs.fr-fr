---
title: Supprimer les objets | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-objects
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.deleteobjects.f1
helpviewer_keywords: Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 37913d6119638c9bd6da6b5dfe84e63817ecffbc
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="delete-objects"></a>Supprimer les objets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Cette boîte de dialogue vous permet de supprimer une base de données ou un objet de base de données.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
**Objet à supprimer**  
Indique les noms, les types, les propriétaires et l'état des objets qui seront supprimés, ainsi que tous les messages sur les erreurs au cours de l'exécution.  
  
> [!NOTE]  
> Exécuter **Supprimer** sur une base de données équivaut à exécuter DROP DATABASE dans [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Afficher les dépendances**  
Cliquez ici pour afficher à la fois les objets qui dépendent de l'objet actuellement sélectionné et les objets dont dépend l'objet actuel (dépendance ascendante et descendante). Les informations affichées dans la boîte de dialogue **Afficher les dépendances** sont en lecture seule.  
  
> [!NOTE]  
> Le bouton **Afficher les dépendances** n'est pas affiché pour tous les types d'objets de base de données. Pour afficher les dépendances quand le bouton **Afficher les dépendances** n’est pas disponible, cliquez avec le bouton droit sur l’objet dans l’Explorateur d’objets, puis cliquez sur **Afficher les dépendances**.  
  
**Supprimer les informations d'historique de sauvegarde et de restauration pour les bases de données**  
Cette case à cocher apparaît seulement quand une base de données est supprimée et elle permet de supprimer l’historique de sauvegarde et de restauration pour la base de données d’objet dans la base de données **msdb** .  
  
**Fermer les connexions existantes**  
Cette case à cocher apparaît seulement lorsqu'une base de données est supprimée et elle permet de mettre fin aux connexions à la base de données d'objet.  
  
