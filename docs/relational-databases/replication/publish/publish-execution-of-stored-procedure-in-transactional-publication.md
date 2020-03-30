---
title: Publier l’exécution d’une procédure stockée (Transactionnel)
description: Découvrez comment publier l’exécution de procédures stockées à l’aide de SQL Server Management Studio.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: b26656d1610b2e813aaf82ece3564af6fc544b11
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287590"
---
# <a name="publish-execution-of-stored-procedure-in-transactional-publication"></a>Publier l’exécution d’une procédure stockée dans une publication transactionnelle
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Spécifiez que l’exécution d’une procédure stockée (et non sa définition uniquement) doit être publiée dans la boîte de dialogue **Propriétés de l’article - \<Article>** . Cette boîte de dialogue est disponible dans l’Assistant Nouvelle publication et dans la boîte de dialogue **Propriétés de la publication - \<Publication>** . Pour plus d’informations sur l’utilisation de l’Assistant et sur l’accès à la boîte de dialogue, consultez [Créer une publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés d’une publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 La définition de la procédure (l'instruction CREATE PROCEDURE) est répliquée vers l'Abonné quand l'abonnement est initialisé ; quand la procédure est exécutée sur le serveur de publication, la réplication exécute la procédure correspondante sur l'Abonné.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>Pour publier l'exécution d'une procédure stockée  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication - \<Publication>** , sélectionnez une procédure stockée.  
  
2.  Cliquez sur **Propriétés de l'article**, puis sur **Définir les propriétés de la procédure stockée en surbrillance**.  
  
3.  Dans la boîte de dialogue **Propriétés de l’article - \<Article>** , spécifiez l’une des valeurs suivantes pour l’option **Répliquer** :  
  
    -   **Exécution de la procédure stockée**  
  
    -   **Exécution de la procédure stockée dans une transaction sérialisée**  
  
         Cette option est recommandée car elle réplique l'exécution de la procédure uniquement si la procédure est exécutée dans le cadre d'une transaction sérialisée. Si la procédure stockée est exécutée hors d'une transaction sérialisée, les modifications apportées aux données des tables publiées sont répliquées en tant que séries d'instructions DML (Data Manipulation Language).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Si vous êtes dans la boîte de dialogue **Propriétés de la publication - \<Publication>** , cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication de l’exécution de procédures stockées dans la réplication transactionnelle](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
