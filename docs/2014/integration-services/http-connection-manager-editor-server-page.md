---
title: Éditeur du gestionnaire de connexions HTTP (page serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.httpconnection.server.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: 774778a0-ece6-4971-b93f-b121d8fc1fc1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 197a2668beb60acf2473a1f53786d7b553e08cf6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058244"
---
# <a name="http-connection-manager-editor-server-page"></a>Éditeur du gestionnaire de connexions HTTP (page Serveur)
  Utilisez l'onglet **Serveur** de la boîte de dialogue **Éditeur du gestionnaire de connexions HTTP** pour configurer le gestionnaire de connexions HTTP en spécifiant des propriétés telles que l'URL et les informations d'identification de sécurité. Une connexion HTTP permet à un package d'accéder à un serveur Web via HTTP pour l'envoi et la réception de fichiers. Une fois le gestionnaire de connexions HTTP configuré, vous pouvez également tester la connexion.  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions HTTP prend en charge uniquement l'authentification anonyme et l'authentification de base. Il ne prend pas en charge l'authentification Windows.  
  
 Pour en savoir plus sur le gestionnaire de connexions HTTP, consultez [HTTP Connection Manager](connection-manager/http-connection-manager.md). Pour en savoir plus sur un scénario d'utilisation courante pour le gestionnaire de connexions HTTP, consultez [Web Service Task](control-flow/web-service-task.md).  
  
## <a name="options"></a>Options  
 **URL du serveur**  
 Tapez l'URL du serveur.  
  
 Si vous projetez d'utiliser le bouton **Télécharger WSDL** de la page **Général** de l' **Éditeur de tâche de service Web** pour télécharger un fichier WSDL, tapez l'URL de ce fichier WSDL. Cette URL se termine par « ?wsdl ».  
  
 **Utiliser les informations d’identification**  
 Spécifiez si vous voulez que le gestionnaire de connexions HTTP utilise les informations d'identification de sécurité de l'utilisateur pour l'authentification.  
  
 **Nom d'utilisateur**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Mot de passe**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Domain**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Utiliser un certificat client**  
 Spécifiez si vous voulez que le gestionnaire de connexions HTTP utilise un certificat client pour l'authentification.  
  
 **Certificat**  
 Sélectionnez un certificat dans la liste via la boîte de dialogue **Sélectionner un certificat** . La zone de texte affiche le nom associé au certificat.  
  
 **Délai d’attente (en secondes)**  
 Spécifiez un délai d'expiration pour la connexion au serveur Web. La valeur par défaut de cette propriété est 30 secondes.  
  
 **Taille de segment (en Ko)**  
 Spécifiez une taille de segment pour l'écriture des données.  
  
 **Tester la connexion**  
 Après avoir configuré le gestionnaire de connexions HTTP, vérifiez que la connexion est viable en cliquant sur **Tester la connexion**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du gestionnaire de connexions HTTP &#40;page proxy&#41;](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)  
  
  
