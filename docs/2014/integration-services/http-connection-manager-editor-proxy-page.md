---
title: Éditeur du gestionnaire de connexions HTTP (page proxy) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.httpconnection.proxy.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: e831a830-49a3-49c5-8a31-9731fc4fd12e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0b6694741388e649e8a216efad18f48a66de6d61
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058260"
---
# <a name="http-connection-manager-editor-proxy-page"></a>Éditeur du gestionnaire de connexions HTTP (page Proxy)
  Utilisez l'onglet **Proxy** de la boîte de dialogue **Éditeur du gestionnaire de connexions HTTP** pour configurer le gestionnaire de connexions HTTP afin d'utiliser un serveur proxy. Une connexion HTTP permet à un package d'accéder à un serveur Web via HTTP pour l'envoi et la réception de fichiers.  
  
 Pour en savoir plus sur le gestionnaire de connexions HTTP, consultez [HTTP Connection Manager](connection-manager/http-connection-manager.md). Pour en savoir plus sur un scénario d'utilisation courante pour le gestionnaire de connexions HTTP, consultez [Web Service Task](control-flow/web-service-task.md).  
  
## <a name="options"></a>Options  
 **Utiliser le proxy**  
 Indiquez si vous voulez que le gestionnaire de connexions HTTP se connecte via un serveur proxy.  
  
 **URL du proxy**  
 Tapez l'URL du serveur proxy.  
  
 **Ignorer le proxy sur l’local**  
 Indiquez si vous voulez que le gestionnaire de connexions HTTP contourne le serveur proxy pour les adresses locales.  
  
 **Utiliser les informations d’identification**  
 Indiquez si vous voulez que le gestionnaire de connexions HTTP utilise les informations d'identification de sécurité pour le serveur proxy.  
  
 **Nom d'utilisateur**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Mot de passe**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Domain**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Liste de contournement du proxy**  
 Liste d'adresses pour lesquelles vous ne souhaitez pas utiliser le serveur proxy.  
  
 **Ajouter**  
 Tapez une adresse pour laquelle vous souhaitez que le gestionnaire de connexions HTTP n'utilise pas le serveur proxy.  
  
 **Remove**  
 Sélectionnez une adresse, puis supprimez-la en cliquant sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du gestionnaire de connexions HTTP &#40;page du serveur&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
  
