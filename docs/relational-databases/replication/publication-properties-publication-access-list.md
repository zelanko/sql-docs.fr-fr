---
title: "Propri&#233;t&#233;s de la publication, Liste d&#39;acc&#232;s aux publications | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.publicationaccesslist.f1"
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Propri&#233;t&#233;s de la publication, Liste d&#39;acc&#232;s aux publications
  Le **liste d’accès** page de le **Propriétés de la Publication** boîte de dialogue permet d’ajouter et supprimer des connexions, les comptes et groupes de la liste d’accès (aux publications PAL). Cette dernière constitue le mécanisme principal assurant la sécurité du serveur de publication. Lorsque vous créez une publication, la réplication crée une liste d'accès aux publications pour cette première. Cette liste, fonctionnant de la même façon qu'une liste de contrôle d'accès [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, contient une liste d'informations de connexions, de comptes et de groupes bénéficiant de l'autorisation d'accès à la publication.  
  
 Lorsqu'un Abonné se connecte au serveur de publication ou au serveur de distribution pour demander l'accès à la publication, ses informations de connexion sont comparées aux informations d'authentification contenues dans la liste d'accès aux publications. Ceci permet d'assurer un niveau de sécurité supplémentaire vis-à-vis du serveur de publication en empêchant l'utilisation des informations de connexion du serveur de publication et du serveur de distribution par un outil client pouvant procéder à des modifications directement sur le serveur de publication. Pour plus d’informations, consultez [sécuriser le serveur de publication](../../relational-databases/replication/security/secure-the-publisher.md).  
  
## Options  
 **Ajouter**  
 Permet d'ajouter une nouvelle entrée à la liste. Vous ne pouvez ajouter que les noms de connexion, de compte ou de groupe déjà définis aussi bien sur le serveur de publication que le serveur de distribution. Ils sont par ailleurs définis sur ces deux serveurs si les comptes du domaine sont utilisés ou si des comptes locaux ont été créés sur les deux serveurs.  
  
 **Supprimer**  
 Supprime de la liste l'entrée sélectionnée.  
  
 **Supprimer tout**  
 Supprime toutes les entrées de la liste.  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d'une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  