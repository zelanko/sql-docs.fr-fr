---
title: Supprimer les objets | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 45752cebe285a109463eaa1c8e529f0c45a6734b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144193"
---
# <a name="delete-objects"></a>Supprimer les objets
  Cette boîte de dialogue vous permet de supprimer une base de données ou un objet de base de données.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Objet à supprimer**  
 Indique les noms, les types, les propriétaires et l'état des objets qui seront supprimés, ainsi que tous les messages sur les erreurs au cours de l'exécution.  
  
> [!NOTE]  
>  Exécuter **Supprimer** sur une base de données équivaut à exécuter DROP DATABASE dans [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Afficher les dépendances**  
 Cliquez ici pour afficher à la fois les objets qui dépendent de l'objet actuellement sélectionné et les objets dont dépend l'objet actuel (dépendance ascendante et descendante). Les informations affichées dans la boîte de dialogue **Afficher les dépendances** sont en lecture seule.  
  
> [!NOTE]  
>  Le bouton **Afficher les dépendances** n'est pas affiché pour tous les types d'objets de base de données. Pour afficher les dépendances quand le bouton **Afficher les dépendances** n’est pas disponible, cliquez avec le bouton droit sur l’objet dans l’Explorateur d’objets, puis cliquez sur **Afficher les dépendances**.  
  
 **Supprimer les informations d'historique de sauvegarde et de restauration pour les bases de données**  
 Cette case à cocher apparaît seulement quand une base de données est supprimée et elle permet de supprimer l’historique de sauvegarde et de restauration pour la base de données d’objet dans la base de données **msdb** .  
  
 **Fermer les connexions existantes**  
 Cette case à cocher apparaît seulement lorsqu'une base de données est supprimée et elle permet de mettre fin aux connexions à la base de données d'objet.  
  
  