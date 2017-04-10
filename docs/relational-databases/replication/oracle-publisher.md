---
title: "Serveur de publication Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.selectoraclepublisher.f1"
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Serveur de publication Oracle
  À partir de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous permet de publier des données d’une base de données Oracle à l’aide de la réplication transactionnelle et capture instantanée. Pour plus d’informations, consultez [vue d’ensemble de la publication Oracle](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
 Le serveur de publication Oracle doit utiliser un serveur de distribution distant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; cet Assistant doit être exécuté sur ce serveur après l'installation et le test du logiciel réseau Oracle nécessaire. Pour plus d’informations, consultez [configurer un serveur de publication Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
> [!IMPORTANT]  
>  Si un autre administrateur configuré la base de données Oracle comme serveur de publication, après avoir cliqué sur **Suivant** vous demandera d’entrer le mot de passe pour la connexion de réplication pour se connecter à la base de données Oracle. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Crée un mappage entre votre nom d’utilisateur et la connexion de serveur lié à la base de données Oracle. Vous ne devez pas entrer un mot de passe pour les connexions ultérieures à la base de données Oracle.  
  
## Options  
 **Serveurs de publication Oracle**  
 Sélectionnez un serveur de publication Oracle dans la liste. Cette liste contient les serveurs de publication Oracle, qui ont été configurés au préalable pour utiliser le serveur, sur lequel s'exécute l'Assistant en tant que serveur de distribution. Si la liste est vide, ou le serveur de publication Oracle dont vous souhaitez utiliser n’est pas dans la liste, cliquez sur **Ajouter le serveur de publication Oracle**.  
  
 **Ajouter un serveur de publication Oracle**  
 Cliquez pour ouvrir la **des propriétés de serveur de distribution** boîte de dialogue. Dans cette boîte de dialogue, cliquez sur **Ajouter**, puis cliquez sur **Ajouter le serveur de publication Oracle**. Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom du serveur Oracle et la connexion et le mot de passe pour le schéma utilisateur administratif de réplication. Pour plus d’informations, consultez [se connecter au serveur de & #40 ; Oracle & #41 ; connexion](../../relational-databases/replication/connect-to-server-oracle-login.md).  
  
> [!NOTE]  
>  Si le serveur, sur lequel s'exécute l'Assistant, n'a pas été configuré en tant que serveur de distribution, le système vous demande alors de le faire.  
  
## Voir aussi  
 [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)   
 [Référence des propriétés de & #40 ; Réplication & #41 ;](../../relational-databases/replication/properties-reference-replication.md)  
  
  