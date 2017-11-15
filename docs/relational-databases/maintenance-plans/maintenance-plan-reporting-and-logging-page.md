---
title: "Plan de maintenance (page Création de rapports et enregistrement) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.maint.reportinglogging.f1
ms.assetid: 3a30b17a-3deb-446f-900a-62f88934a90f
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b94a7b05ebe694c668bfb9e8763e1be479cddf51
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="maintenance-plan-reporting-and-logging-page"></a>Plan de maintenance, (Page Création de rapports et enregistrement)
  La boîte de dialogue **Création de rapport et enregistrement** vous permet de configurer les rapports et les enregistrements qui sont générés lors de l'exécution des plans de maintenance.  
  
## <a name="options"></a>Options  
 **Générer un rapport de fichier texte**  
 Indiquez si [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit générer un rapport de fichier texte.  
  
 **Créer un nouveau fichier**  
 Crée un nouveau fichier de rapport pour chaque exécution du plan de maintenance. Par défaut, les fichiers de rapport sont enregistrés sur l'ordinateur hébergeant l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant ce plan de maintenance, dans le dossier qui a été défini en tant que dossier des journaux par défaut au moment de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour spécifier un autre dossier, entrez le chemin d’accès complet du dossier dans la zone de texte **Dossier** ou cliquez sur le bouton Parcourir (**...**) pour naviguer jusqu’au dossier de votre choix.  
  
 **Ajouter au fichier**  
 Ajoutez le rapport généré pour chaque exécution du plan au fichier spécifié dans la zone de texte **Nom de fichier** . Vous pouvez également spécifier un autre fichier en cliquant sur le bouton Parcourir et en sélectionnant un fichier dans la boîte de dialogue.  
  
 **Envoyer le rapport à un destinataire de messagerie**  
 Transmet le résultat de l'exécution d'un plan de maintenance par courrier électronique. Cette option est uniquement disponible si la messagerie de base de données est activée et correctement configurée.  
  
 **Opérateur d'agent**  
 Sélectionnez dans la liste l'opérateur d'agent qui sera le destinataire du message électronique. Cette option est uniquement disponible si la messagerie est activée et correctement configurée.  
  
 **Enregistrer les informations étendues**  
 Permet d'inclure plus d'informations dans le journal. L'utilisation de cette option augmente la taille de l'historique du plan de maintenance qui est stocké sur l'ordinateur.  
  
 **Connexion à un serveur distant**  
 Enregistre l'historique du plan de maintenance sur un serveur distant.  
  
 **Connexion**  
 Spécifie les informations de connexion à utiliser pour se connecter à un serveur distant.  
  
 **Nouveau**  
 Affiche la boîte de dialogue **Propriétés de connexion** . Sert à configurer les nouvelles informations de connexion permettant de se connecter à un serveur distant.  
  
## <a name="see-also"></a>Voir aussi  
 [Plans de maintenance](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)  
  
  
