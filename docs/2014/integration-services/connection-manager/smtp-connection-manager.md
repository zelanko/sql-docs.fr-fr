---
title: Gestionnaire de connexions SMTP | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a00a8295904d8fdc5a1ad87c6ac60dbf70ce6fa9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051996"
---
# <a name="smtp-connection-manager"></a>Gestionnaire de connexions SMTP
  Un gestionnaire de connexions SMTP permet à un package de se connecter à un serveur SMTP (Simple Mail Transfer Protocol). La tâche Envoyer un message incluse dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise un gestionnaire de connexions SMTP.  
  
 Lorsque vous utilisez Microsoft Exchange comme serveur SMTP, vous pouvez être amené à configurer le gestionnaire de connexions SMTP de manière à utiliser l'authentification Windows. Les serveurs Exchange peuvent être configurés pour ne pas autoriser les connexions SMTP non authentifiées.  
  
## <a name="configuration-the-smtp-connection-manager"></a>Configuration du gestionnaire de connexions SMTP  
 Lorsque vous ajoutez un gestionnaire de connexions SMTP à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée une connexion de gestionnaire qui sera converti en connexion SMTP au moment de l’exécution, définit les propriétés du Gestionnaire des connexions et ajoute le Gestionnaire de connexions pour la `Connections` collection sur le package. Le `ConnectionManagerType` du Gestionnaire de connexions est définie sur `SMTP`.  
  
 Vous pouvez configurer un gestionnaire de connexions SMTP de plusieurs manières :  
  
-   Spécifiez une chaîne de connexion.  
  
-   Indiquez le nom d'un serveur SMTP.  
  
-   Spécifiez la méthode d'authentification à utiliser.  
  
    > [!IMPORTANT]  
    >  Le gestionnaire de connexions SMTP prend en charge uniquement l'authentification anonyme et l'authentification Windows. Il ne prend pas en charge l'authentification de base.  
  
-   Permet d'indiquer si les communications doivent être chiffrées à l'aide de SSL (Secure Sockets Layer) lors de l'envoi de messages électroniques.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur du gestionnaire de connexions SMTP](../smtp-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programme, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  