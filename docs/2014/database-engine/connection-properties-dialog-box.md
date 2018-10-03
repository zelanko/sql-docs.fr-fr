---
title: Propriétés de connexion, boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectionproperties.f1
helpviewer_keywords:
- Connection Properties dialog box
ms.assetid: 6df812ad-4d80-4503-8a23-47719ce85624
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 350e48c225814052655e4fced89d2f934efa188f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155899"
---
# <a name="connection-properties-dialog-box"></a>Propriétés de connexion, boîte de dialogue
  Cette boîte de dialogue vous permet d'afficher les propriétés de la connexion en cours. Cette boîte de dialogue est disponible lorsque vous cliquez sur **Afficher les propriétés de connexion** dans les différentes boîtes de dialogue de l'Explorateur d'objets. Les propriétés affichées dans cette page sont en lecture seule.  
  
 Pour modifier des propriétés telles que **Base de données**, connectez-vous à la base de données de votre choix à l'aide de l'Explorateur d'objets, avant d'ouvrir la boîte de dialogue **Propriétés de connexion** .  
  
 Notez que le délai d'attente de requête pour SQL Azure est de 30 minutes.  
  
## <a name="authentication"></a>Authentification  
 Permet d'afficher les propriétés d'authentification pour la connexion en cours. Les propriétés d'authentification correspondent au nom d'accès et à la méthode d'authentification utilisés une fois la connexion établie. Pour modifier les propriétés d'authentification, déconnectez-vous de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], puis connectez de nouveau l'Explorateur d'objets au serveur, à l'aide des options de connexion de votre choix.  
  
 **Méthode d’authentification**  
 Méthode d'authentification utilisée pour la connexion en cours.  
  
 **Nom d'utilisateur**  
 Nom de l'utilisateur de connexion utilisé pour l'authentification de la connexion.  
  
## <a name="connection-category"></a>Catégorie de connexion  
 Permet d'afficher les propriétés de la connexion en cours. La plupart des propriétés de connexion ont été sélectionnées sous l'onglet **Propriétés de connexion** de la boîte de dialogue **Se connecter au serveur** au cours du processus de connexion.  
  
 **Sauvegarde de la base de données**  
 Nom de la base de données connectée. Pour modifier cela, utilisez la barre d'outils Éditeur SQL.  
  
 **SPID**  
 Identificateur de processus système attribué par le serveur à la connexion. Il ne peut pas être changé pour cette connexion.  
  
 **Protocole réseau**  
 Protocole réseau de la connexion [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] . Pour modifier cela, connectez-vous de nouveau à l'aide des propriétés de connexion souhaitées.  
  
 **Taille du paquet réseau**  
 Taille de paquet utilisée lors de la communication avec le serveur. Pour modifier cela, connectez-vous de nouveau à l'aide des propriétés de connexion souhaitées.  
  
 **Délai de connexion**  
 Durée en secondes à attendre lors de la connexion à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avant l'expiration du délai et le renvoi à l'utilisateur d'une erreur de type Échec de connexion. Pour modifier cela, connectez-vous de nouveau à l'aide des propriétés de connexion souhaitées.  
  
 **Délai d'exécution**  
 Durée en secondes à attendre avant que l'exécution d'une tâche se termine sur le serveur. Pour modifier cela, connectez-vous de nouveau à l'aide des propriétés de connexion souhaitées.  
  
 **Chiffré**  
 Indique si la connexion en cours est chiffrée ou non. Pour modifier cela, connectez-vous de nouveau à l'aide des propriétés de connexion souhaitées.  
  
## <a name="product-category"></a>Catégorie de produit  
 Permet d'afficher les propriétés des produits pour la connexion en cours. Ces propriétés décrivent le produit, la version, le nom de l'instance et le classement du serveur. Les propriétés sont définies au cours de l'installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **Nom du produit**  
 Nom du produit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **Version du produit**  
 Version du produit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **Nom de serveur**  
 Nom de l'ordinateur qui exécute [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **Nom d'instance**  
 Nom de l'instance du serveur. L'instance par défaut est vide.  
  
 **Langage**  
 Version du langage du produit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **Classement**  
 Classement du serveur.  
  
## <a name="server-environment-category"></a>Catégorie d'environnement de serveur  
 Permet d'afficher les propriétés d'environnement de serveur de la connexion en cours en rapport avec le matériel et le système d'exploitation de serveur. Les propriétés ne peuvent pas être configurées par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **Nom d’ordinateur**  
 Nom de l'ordinateur serveur qui exécute [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **Plateforme**  
 Nom du système d'exploitation, nom du fabricant et famille d'UC du serveur.  
  
 **Système d'exploitation**  
 Version de [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows installée sur le serveur.  
  
 **Processeurs**  
 Nombre de processeurs sur le serveur.  
  
 **Operating System Memory**  
 Quantité globale de mémoire physique sur le serveur, en mégaoctets.  
  
## <a name="see-also"></a>Voir aussi  
 [Pages de propriétés dans SQL Server Management Studio](../ssms/property-pages-in-sql-server-management-studio.md)   
 [Se connecter au serveur &#40;page Connexion&#41; — Moteur de base de données](../ssms/f1-help/connect-to-server-login-page-database-engine.md)  
  
  
