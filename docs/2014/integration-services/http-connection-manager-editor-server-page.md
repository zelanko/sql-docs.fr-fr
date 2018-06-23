---
title: Éditeur du Gestionnaire de connexions HTTP (Page serveur) | Documents Microsoft
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
- sql12.dts.designer.httpconnection.server.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: 774778a0-ece6-4971-b93f-b121d8fc1fc1
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9c298c6bb6427b42f0302350919081e2c3e5bc08
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041413"
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
  
 **Utiliser les informations d'identification**  
 Spécifiez si vous voulez que le gestionnaire de connexions HTTP utilise les informations d'identification de sécurité de l'utilisateur pour l'authentification.  
  
 **Nom d'utilisateur**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Mot de passe**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Domaine**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Utiliser le certificat client**  
 Spécifiez si vous voulez que le gestionnaire de connexions HTTP utilise un certificat client pour l'authentification.  
  
 **Certificat**  
 Sélectionnez un certificat dans la liste via la boîte de dialogue **Sélectionner un certificat** . La zone de texte affiche le nom associé au certificat.  
  
 **Délai d'expiration (en secondes)**  
 Spécifiez un délai d'expiration pour la connexion au serveur Web. La valeur par défaut de cette propriété est 30 secondes.  
  
 **Taille de segment (en Ko)**  
 Spécifiez une taille de segment pour l'écriture des données.  
  
 **Tester la connexion**  
 Après avoir configuré le gestionnaire de connexions HTTP, vérifiez que la connexion est viable en cliquant sur **Tester la connexion**.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du Gestionnaire de connexions HTTP &#40;Page Proxy&#41;](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)  
  
  