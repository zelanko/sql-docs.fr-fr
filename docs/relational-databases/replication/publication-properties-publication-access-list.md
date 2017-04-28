---
title: "Propriétés de la publication, Liste d’accès aux publications | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.publicationaccesslist.f1
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d088078d9f36e1ca6fc0bc49cb324f95dd2f1db2
ms.lasthandoff: 04/11/2017

---
# <a name="publication-properties-publication-access-list"></a>Propriétés de la publication, Liste d'accès aux publications
  La page **Liste d'accès aux publications** de la boîte de dialogue **Propriétés de la publication** vous permet d'ajouter et de supprimer des informations de connexion, des comptes et des groupes de la liste d'accès aux publications. Cette dernière constitue le mécanisme principal assurant la sécurité du serveur de publication. Lorsque vous créez une publication, la réplication crée une liste d'accès aux publications pour cette première. Cette liste, fonctionnant de la même façon qu'une liste de contrôle d'accès [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, contient une liste d'informations de connexions, de comptes et de groupes bénéficiant de l'autorisation d'accès à la publication.  
  
 Lorsqu'un Abonné se connecte au serveur de publication ou au serveur de distribution pour demander l'accès à la publication, ses informations de connexion sont comparées aux informations d'authentification contenues dans la liste d'accès aux publications. Ceci permet d'assurer un niveau de sécurité supplémentaire vis-à-vis du serveur de publication en empêchant l'utilisation des informations de connexion du serveur de publication et du serveur de distribution par un outil client pouvant procéder à des modifications directement sur le serveur de publication. Pour plus d’informations, consultez [Sécuriser le serveur de publication](../../relational-databases/replication/security/secure-the-publisher.md).  
  
## <a name="options"></a>Options  
 **Ajouter**  
 Permet d'ajouter une nouvelle entrée à la liste. Vous ne pouvez ajouter que les noms de connexion, de compte ou de groupe déjà définis aussi bien sur le serveur de publication que le serveur de distribution. Ils sont par ailleurs définis sur ces deux serveurs si les comptes du domaine sont utilisés ou si des comptes locaux ont été créés sur les deux serveurs.  
  
 **Supprimer**  
 Supprime de la liste l'entrée sélectionnée.  
  
 **Supprimer tout**  
 Supprime toutes les entrées de la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
