---
title: "&#201;diteur du gestionnaire de connexions HTTP (page Proxy) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.httpconnection.proxy.f1"
helpviewer_keywords: 
  - "Éditeur du gestionnaire de connexions HTTP"
ms.assetid: e831a830-49a3-49c5-8a31-9731fc4fd12e
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# &#201;diteur du gestionnaire de connexions HTTP (page Proxy)
  Utilisez l'onglet **Proxy** de la boîte de dialogue **Éditeur du gestionnaire de connexions HTTP** pour configurer le gestionnaire de connexions HTTP afin d'utiliser un serveur proxy. Une connexion HTTP permet à un package d'accéder à un serveur Web via HTTP pour l'envoi et la réception de fichiers.  
  
 Pour en savoir plus sur le gestionnaire de connexions HTTP, consultez [HTTP Connection Manager](../../integration-services/connection-manager/http-connection-manager.md). Pour en savoir plus sur un scénario d'utilisation courante pour le gestionnaire de connexions HTTP, consultez [Web Service Task](../../integration-services/control-flow/web-service-task.md).  
  
## Options  
 **Utiliser le proxy**  
 Indiquez si vous voulez que le gestionnaire de connexions HTTP se connecte via un serveur proxy.  
  
 **URL du proxy**  
 Tapez l'URL du serveur proxy.  
  
 **Ne pas utiliser de proxy en local**  
 Indiquez si vous voulez que le gestionnaire de connexions HTTP contourne le serveur proxy pour les adresses locales.  
  
 **Utiliser les informations d'identification**  
 Indiquez si vous voulez que le gestionnaire de connexions HTTP utilise les informations d'identification de sécurité pour le serveur proxy.  
  
 **Nom d'utilisateur**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Mot de passe**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Domaine**  
 Si le gestionnaire de connexions HTTP utilise des informations d'identification, vous devez spécifier un nom d'utilisateur, un mot de passe et un domaine.  
  
 **Liste de contournement proxy**  
 Liste d'adresses pour lesquelles vous ne souhaitez pas utiliser le serveur proxy.  
  
 **Ajouter**  
 Tapez une adresse pour laquelle vous souhaitez que le gestionnaire de connexions HTTP n'utilise pas le serveur proxy.  
  
 **Supprimer**  
 Sélectionnez une adresse, puis supprimez-la en cliquant sur **Supprimer**.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du gestionnaire de connexions HTTP &#40;page Serveur&#41;](../../integration-services/connection-manager/http-connection-manager-editor-server-page.md)  
  
  