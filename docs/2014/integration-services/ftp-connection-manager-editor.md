---
title: Éditeur du Gestionnaire de connexions FTP | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.ftpconnectionmanager.f1
helpviewer_keywords:
- FTP Connection Manager Editor
ms.assetid: 874b6585-255b-4a43-8396-bb08c3e8ac2b
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 063d8a0c044739bbc6e7a1994176962fcf769093
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140560"
---
# <a name="ftp-connection-manager-editor"></a>Éditeur du gestionnaire de connexions FTP
  La boîte de dialogue **Éditeur du gestionnaire de connexions FTP** vous permet de spécifier les propriétés de connexion à un serveur FTP.  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions FTP prend en charge uniquement l'authentification anonyme et l'authentification de base. Il ne prend pas en charge l'authentification Windows.  
  
 Pour en savoir plus sur le gestionnaire de connexions FTP, consultez [Gestionnaire de connexions FTP](connection-manager/ftp-connection-manager.md).  
  
## <a name="options"></a>Options  
 **Nom du serveur**  
 Indiquez le nom du serveur FTP.  
  
 **Port du serveur**  
 Spécifiez le numéro de port sur le serveur FTP à utiliser pour la connexion. La valeur par défaut de cette propriété est **21**.  
  
 **Nom d'utilisateur**  
 Indiquez un nom d'utilisateur pour accéder au serveur FTP. La valeur par défaut de cette propriété est **anonyme**.  
  
 **Mot de passe**  
 Indiquez le mot de passe permettant d'accéder au serveur FTP.  
  
 **Délai d'expiration (en secondes)**  
 Spécifiez le nombre de secondes à patienter avant l'expiration de la tâche. Une valeur égale à **0** indique une durée illimitée. La valeur par défaut de cette propriété est **60**.  
  
 **Utiliser le mode passif**  
 Permet de spécifier si le serveur ou le client initie la connexion. Le serveur initie la connexion en mode actif, alors que le client l'initie en mode passif. La valeur par défaut de cette propriété est **mode actif**.  
  
 **Tentatives**  
 Spécifiez le nombre de fois que la tâche doit tenter d'établir une connexion. Une valeur égale à **0** indique un nombre illimité de tentatives.  
  
 **Taille de segment (en Ko)**  
 Spécifiez une taille de segment en kilo-octets pour la transmission des données.  
  
 **Tester la connexion**  
 Après avoir configuré le gestionnaire de connexions FTP, confirmez que la connexion est viable en cliquant sur **Tester la connexion**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  