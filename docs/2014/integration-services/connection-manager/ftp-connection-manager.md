---
title: Gestionnaire de connexions FTP | Microsoft Docs
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
- FTP connection manager
- connections [Integration Services], FTP
- connection managers [Integration Services], FTP
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5e96a1a11651106cd0534ec20a3a35b79a9f1e7e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152669"
---
# <a name="ftp-connection-manager"></a>Gestionnaires de connexion FTP
  Un gestionnaire de connexions FTP permet à un package de se connecter à un serveur FTP (File Transfer Protocol). La tâche FTP incluse dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise ce gestionnaire de connexions.  
  
 Lorsque vous ajoutez un gestionnaire de connexions FTP à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui peut être résolu en tant que connexion FTP au moment de l'exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection `Connections` sur le package.  
  
 Le `ConnectionManagerType` du Gestionnaire de connexions est définie sur `FTP`.  
  
 Vous pouvez configurer le gestionnaire de connexions FTP de plusieurs manières :  
  
-   Spécifiez un nom de serveur et un port de serveur.  
  
-   Spécifiez l'accès anonyme ou fournissez un nom d'utilisateur et un mot de passe pour l'authentification de base.  
  
    > [!IMPORTANT]  
    >  Le gestionnaire de connexions FTP prend en charge uniquement l'authentification anonyme et l'authentification de base. Il ne prend pas en charge l'authentification Windows.  
  
-   Définissez le délai d'attente, le nombre de nouvelles tentatives et la quantité de données à copier en une fois.  
  
-   Indiquez si le gestionnaire de connexions FTP utilise le mode actif ou passif.  
  
 Selon la configuration du site FTP auquel le gestionnaire de connexions FTP se connecte, vous devrez éventuellement changer les valeurs par défaut suivantes du gestionnaire de connexions :  
  
-   Le port du serveur est réglé sur 21. Vous devez spécifier le port que le site FTP écoute.  
  
-   Le nom d'utilisateur prend la valeur « anonymous ». Vous devez fournir les informations d'identification requises par le site FTP.  
  
## <a name="activepassive-modes"></a>Modes actif/passif  
 Un gestionnaire de connexions FTP peut envoyer et recevoir des fichiers en mode actif ou passif. En mode actif, le serveur initie la connexion de données, alors qu'en mode passif il s'agit du client.  
  
## <a name="configuration-of-the-ftp-connection-manager"></a>Configuration du gestionnaire de connexions FTP  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur du gestionnaire de connexions FTP](../ftp-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programme, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche FTP](../control-flow/ftp-task.md)   
 [Services d’intégration &#40;SSIS&#41; connexions](integration-services-ssis-connections.md)  
  
  