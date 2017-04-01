---
title: "Gestionnaire de connexions FTP | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Gestionnaires de connexion FTP"
  - "connexions [Integration Services], FTP"
  - "gestionnaires de connexions [Integration Services], FTP"
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 41
---
# Gestionnaire de connexions FTP
  Un gestionnaire de connexions FTP permet à un package de se connecter à un serveur FTP (File Transfer Protocol). La tâche FTP incluse dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise ce gestionnaire de connexions.  
  
 Quand vous ajoutez un gestionnaire de connexions FTP à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui peut être résolu en tant que connexion FTP au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connexions** sur le package.  
  
 La propriété **ConnectionManagerType** du gestionnaire de connexions a pour valeur **FTP**.  
  
 Vous pouvez configurer le gestionnaire de connexions FTP de plusieurs manières :  
  
-   Spécifiez un nom de serveur et un port de serveur.  
  
-   Spécifiez l'accès anonyme ou fournissez un nom d'utilisateur et un mot de passe pour l'authentification de base.  
  
    > [!IMPORTANT]  
    >  Le gestionnaire de connexions FTP prend en charge uniquement l'authentification anonyme et l'authentification de base. Il ne prend pas en charge l'authentification Windows.  
  
-   Définissez le délai d'attente, le nombre de nouvelles tentatives et la quantité de données à copier en une fois.  
  
-   Indiquez si le gestionnaire de connexions FTP utilise le mode actif ou passif.  
  
 Selon la configuration du site FTP auquel le gestionnaire de connexions FTP se connecte, vous devrez éventuellement changer les valeurs par défaut suivantes du gestionnaire de connexions :  
  
-   Le port du serveur est réglé sur 21. Vous devez spécifier le port que le site FTP écoute.  
  
-   Le nom d'utilisateur prend la valeur « anonymous ». Vous devez fournir les informations d'identification requises par le site FTP.  
  
## Modes actif/passif  
 Un gestionnaire de connexions FTP peut envoyer et recevoir des fichiers en mode actif ou passif. En mode actif, le serveur initie la connexion de données, alors qu'en mode passif il s'agit du client.  
  
## Configuration du gestionnaire de connexions FTP  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], consultez [Éditeur du gestionnaire de connexions FTP](../../integration-services/connection-manager/ftp-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## Voir aussi  
 [Tâche FTP](../../integration-services/control-flow/ftp-task.md)   
 [Connexions Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  