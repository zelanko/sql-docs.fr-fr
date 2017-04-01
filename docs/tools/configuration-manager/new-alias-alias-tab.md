---
title: "Nouvel alias (onglet Alias) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 785eb6fb-f67e-449d-b1c8-c38dfbb95ef6
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Nouvel alias (onglet Alias)
  Un alias est un nom de remplacement permettant d'établir une connexion. L'alias encapsule les éléments requis d'une chaîne de connexion, puis les expose sous un nom choisi par l'utilisateur. La page **Alias** de la boîte de dialogue **Alias - Nouveau** vous permet de spécifier les éléments de la chaîne de connexion d’un alias. Pour modifier la chaîne de connexion d’un alias existant, consultez [Propriétés de &#60;Alias&#62; &#40;onglet Alias&#41;](../../tools/configuration-manager/alias-properties-alias-tab.md).  
  
 Il n'est pas nécessaire de renseigner toutes les valeurs de la grille **Propriétés** . Le protocole sélectionné détermine les combinaisons valides. Voir les rubriques indiquées ci-après pour obtenir des exemples de combinaisons valides.  
  
 **Nom de l'alias**  
 Nom (alias) à utiliser pour faire référence à cette connexion.  
  
 **Nom du canal** / **Numéro de port**  
 Éléments supplémentaires de la chaîne de connexion. Le nom de cette zone varie en fonction du protocole sélectionné.  
  
 **Protocole**  
 Protocole utilisé pour la connexion.  
  
 **Server**  
 Nom de l’instance [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers laquelle la connexion est établie.  
  
## Cas d'utilisation d'un alias  
 Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connecte à une instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le protocole de **mémoire partagée**, et à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un autre ordinateur à l’aide du protocole **TCP/IP** ou de **Canaux nommés**. Créez un alias lorsque vous utilisez le protocole TCP/IP ou des canaux nommés, et que vous souhaitez fournir une chaîne de connexion personnalisée ou utiliser un nom différent du nom de serveur pour la connexion.  
  
### Exemples  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’étant pas à l’écoute sur le port TCP/IP 1433 par défaut, vous pouvez fournir une chaîne de connexion comportant un numéro de port différent.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'étant pas à l'écoute sur le canal nommé par défaut, vous pouvez fournir une chaîne de connexion comportant un nom de canal différent.  
  
-   Une application doit normalement se connecter à une base de données située sur le serveur nommé `ACCT`, mais cette base de données a été consolidée sous la forme d'une instance nommée `ACCT` sur un serveur nommé `CENTRAL`. L'application ne peut pas être facilement modifiée. Créez un alias nommé `ACCT`, avec une chaîne de connexion pointant vers `CENTRAL\ACCT`.  
  
## Création d'une chaîne de connexion valide  
 Les rubriques suivantes décrivent et illustrent des combinaisons valides de propriétés d'alias :  
  
-   [Création d'une chaîne de connexion valide à l'aide du protocole de mémoire partagée](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
-   [Création d’une chaîne de connexion valide à l’aide du protocole TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
-   [Création d'une chaîne de connexion valide à l'aide de canaux nommés](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md)  
  
  