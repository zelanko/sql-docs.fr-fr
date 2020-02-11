---
title: Plan de maintenance (page Création de rapports et enregistrement) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reportinglogging.f1
ms.assetid: 3a30b17a-3deb-446f-900a-62f88934a90f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 623507b4d9e52da376d4c83e4ee5c4d51b15dc39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63186260"
---
# <a name="maintenance-plan-reporting-and-logging-page"></a>Plan de maintenance, (Page Création de rapports et enregistrement)
  Utilisez la boîte de dialogue création de rapports **et enregistrement** pour configurer les rapports et les journaux qui sont générés lorsque des plans de maintenance sont exécutés.  
  
## <a name="options"></a>Options  
 **Générer un rapport de fichier texte**  
 Spécifiez si vous [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] souhaitez écrire un rapport de fichier texte.  
  
 **Créer un nouveau fichier**  
 Crée un nouveau fichier de rapport pour chaque exécution du plan de maintenance. Par défaut, les fichiers de rapport sont enregistrés sur l'ordinateur hébergeant l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant ce plan de maintenance, dans le dossier qui a été défini en tant que dossier des journaux par défaut au moment de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour spécifier un autre dossier, entrez le chemin d’accès complet du dossier dans la zone de texte **Dossier** ou cliquez sur le bouton Parcourir (**...**) pour naviguer jusqu’au dossier de votre choix.  
  
 **Ajouter au fichier**  
 Ajoutez le rapport généré pour chaque exécution du plan au fichier spécifié dans la zone de texte **Nom de fichier** . Vous pouvez également spécifier un autre fichier en cliquant sur le bouton Parcourir et en sélectionnant un fichier dans la boîte de dialogue.  
  
 **Envoyer le rapport à un destinataire de courrier électronique**  
 Transmet le résultat de l'exécution d'un plan de maintenance par courrier électronique. Cette option est uniquement disponible si la messagerie de base de données est activée et correctement configurée.  
  
 **Opérateur d’agent**  
 Sélectionnez dans la liste l'opérateur d'agent qui sera le destinataire du message électronique. Cette option est uniquement disponible si la messagerie est activée et correctement configurée.  
  
 **Enregistrer les informations étendues**  
 Permet d'inclure plus d'informations dans le journal. L'utilisation de cette option augmente la taille de l'historique du plan de maintenance qui est stocké sur l'ordinateur.  
  
 **Se connecter au serveur distant**  
 Enregistre l'historique du plan de maintenance sur un serveur distant.  
  
 **Connection**  
 Spécifie les informations de connexion à utiliser pour se connecter à un serveur distant.  
  
 **Nouveau**  
 Affiche la boîte de dialogue **Propriétés de connexion** . Sert à configurer les nouvelles informations de connexion permettant de se connecter à un serveur distant.  
  
## <a name="see-also"></a>Voir aussi  
 [Plans de maintenance](maintenance-plans.md)   
 [Messagerie de base de données](../database-mail/database-mail.md)  
  
  
