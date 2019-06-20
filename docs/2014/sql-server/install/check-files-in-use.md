---
title: Vérifier les fichiers en cours d’utilisation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccd65867-d4c0-43b2-8361-7fd41c6f79ac
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34b51b26454766498ee601baae3ccc52cd1c5768
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66096529"
---
# <a name="check-files-in-use"></a>Vérifier les fichiers en cours d'utilisation
  Pour éviter d'avoir à redémarrer Windows après avoir installé des mises à jour de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , utilisez la page Vérifier les fichiers en cours d'utilisation afin d'identifier les processus qui verrouillent des fichiers requis par le programme d'installation des mises à jour de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Arrêtez toutes les applications et tous les services qui établissent des connexions aux instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont en cours de mise à jour. Cela implique l'arrêt de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Si le programme d'installation détermine que des fichiers sont verrouillés au cours de l'installation, vous devrez peut-être redémarrer votre ordinateur au terme de l'installation. Si tel est le cas, le programme d'installation vous demandera de le faire. Si le programme d'installation doit arrêter un service au cours de l'installation, il redémarrera ce dernier une fois l'installation terminée.  
  
 Pour vous éviter d'avoir à redémarrer votre ordinateur après l'installation, le programme d'installation affiche la liste des processus qui verrouillent des fichiers. Arrêtez les processus et les applications de la liste. Cliquez sur **Actualiser la vérification** pour réexécuter la vérification. Cliquez sur **Arrêter la vérification** pour mettre fin à une vérification en cours d'exécution. Si aucun fichier verrouillé n'est détecté, le tableau est vide. Une fois que tous les processus bloquants ont été arrêtés, cliquez sur **Suivant** pour continuer.  
  
 Le programme d'installation enregistre les informations dans le fichier journal. Pour plus d’informations sur la façon d’afficher les fichiers journaux, consultez [afficher et lire les fichiers journaux d’installation de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) et [Comment : Lire un fichier de journal d’installation SQL Server](https://go.microsoft.com/fwlink/?LinkID=134490).  
  
 Les informations suivantes sont contenues dans le fichier journal :  
  
-   Nom du processus  
  
-   Nom de la fonctionnalité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Type de processus  
  
-   Compte sous lequel le processus est en cours d'exécution  
  
-   ID de processus  
  
-   Nom du fichier verrouillé  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
  
|Nom|Description|  
|----------|-----------------|  
|Traiter|Affiche le nom complet du processus qui utilise les fichiers à mettre à jour.|  
|type|Affiche le type de processus.|  
|Compte|Affiche le compte sous lequel le processus est en cours d'exécution.|  
|ID de processus|Affiche l'ID de processus.|  
  
  
