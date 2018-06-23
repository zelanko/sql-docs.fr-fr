---
title: Nouveau ou modifier l’enregistrement du serveur (onglet Général) (SSIS) | Documents Microsoft
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
- sql12.swb.registerserver.general.dts.f1
ms.assetid: b586b736-344b-4e42-83ee-96f66ad433a5
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d7ba0339d5bed873ef321bd83a3ee247e5523247
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143956"
---
# <a name="new-or-edit-server-registration-general-tab-ssis"></a>Nouvelle inscription de serveur ou Modifier les propriétés d'inscription du serveur (onglet Général) (SSIS)
  Cet onglet vous permet de spécifier des options lors de l'inscription de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 Pour accéder à cette page, dans Serveurs inscrits, cliquez sur **Integration Services** dans la barre d’outils **Serveurs inscrits** , cliquez avec le bouton droit sur un groupe de serveurs inscrits quelconque, pointez sur **Nouveau**, puis cliquez sur **Inscription du serveur**.  
  
## <a name="options"></a>Options  
 **Type de serveur**  
 Quand un serveur est inscrit dans Serveurs inscrits, la zone **Type de serveur** est en lecture seule et concorde avec le type de serveur affiché dans Serveurs inscrits. Pour inscrire un autre type de serveur, cliquez sur **Moteur de base de données**, **Serveur d'analyse**, **Reporting Services**, **SQL Server Compact** **Edition**ou **Integration Services** dans la barre d'outils **Serveurs inscrits** avant de commencer à inscrire un nouveau serveur.  
  
 **Nom du serveur**  
 Sélectionnez le serveur auquel vous souhaitez vous connecter. Le dernier serveur avec lequel une connexion a été établie apparaît par défaut.  
  
 **Authentification**  
 Le mode d'authentification Windows permet à l'utilisateur de se connecter au moyen d'un compte d'utilisateur [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows.  
  
 **Nom d'utilisateur**  
 Cette option n'est pas disponible dans cette version.  
  
 **Mot de passe**  
 Cette option n'est pas disponible dans cette version.  
  
 **Mémoriser le mot de passe**  
 Cette option n'est pas disponible dans cette version.  
  
 **Nom du serveur inscrit**  
 Nom qui doit apparaître dans **Serveurs inscrits**. Ce nom ne doit pas correspondre à celui de la zone **Nom du serveur** .  
  
 **Description du serveur inscrit**  
 Entrez une description facultative du serveur.  
  
 **Test**  
 Cliquez sur cette option pour tester la connexion au serveur sélectionné dans la zone **Nom du serveur**.  
  
 **Enregistrer**  
 Cliquez sur ce bouton pour enregistrer les paramètres des serveurs inscrits.  
  
  