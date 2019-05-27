---
title: Éditeur du Gestionnaire de connexions SMTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smtpconnection.f1
helpviewer_keywords:
- SMTP Connection Manager Editor
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 527c8f647c963c2c1c03171eeb154a790ab1994a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66055558"
---
# <a name="smtp-connection-manager-editor"></a>Éditeur du gestionnaire de connexions SMTP
  Utilisez la boîte de dialogue **Éditeur du gestionnaire de connexions SMTP** pour spécifier un serveur SMTP (Simple Mail Transfer Protocol).  
  
 Pour en savoir plus sur le gestionnaire de connexions SMTP, consultez [SMTP Connection Manager](connection-manager/smtp-connection-manager.md).  
  
## <a name="options"></a>Options  
 **Nom**  
 Donnez un nom unique au gestionnaire de connexions.  
  
 **Description**  
 Décrivez le gestionnaire de connexions. Il est recommandé d'indiquer ici l'usage auquel le gestionnaire de connexions est destiné, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
 **Serveur SMTP**  
 Indiquez le nom du serveur SMTP.  
  
 **Utiliser l'authentification Windows**  
 Sélectionnez cette option pour envoyer des messages au moyen d'un serveur SMTP utilisant l'authentification Windows pour authentifier l'accès au serveur.  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions SMTP prend en charge uniquement l'authentification anonyme et l'authentification Windows. Il ne prend pas en charge l'authentification de base.  
  
> [!NOTE]  
>  Lorsque vous utilisez Microsoft Exchange comme serveur SMTP, vous devrez peut-être définir **utiliser l’authentification Windows** à `True`. Les serveurs Exchange peuvent être configurés de manière à interdire les connexions SMTP non authentifiées.  
  
 **Activer SSL (Secure Sockets Layer)**  
 Sélectionnez cette option pour chiffrer la communication au moyen de Secure Sockets Layer (SSL) lors de l'envoi de messages électroniques.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
