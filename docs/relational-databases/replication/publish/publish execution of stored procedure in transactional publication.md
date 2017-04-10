---
title: "publier l&#39;ex&#233;cution d&#39;une proc&#233;dure stock&#233;e dans une publication transactionnelle (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "publication [réplication SQL Server], exécution d'une procédure stockée"
  - "procédures stockées [réplication SQL Server], publication"
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# publier l&#39;ex&#233;cution d&#39;une proc&#233;dure stock&#233;e dans une publication transactionnelle (SQL Server Management Studio)
  Spécifier que l’exécution d’une procédure stockée (plutôt que sa définition) doit être publiée dans le **Propriétés de l’Article - \< Article>** boîte de dialogue. Cette boîte de dialogue est disponible dans l’Assistant Nouvelle Publication et **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [Création d’une Publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 La définition de la procédure (l'instruction CREATE PROCEDURE) est répliquée vers l'Abonné quand l'abonnement est initialisé ; quand la procédure est exécutée sur le serveur de publication, la réplication exécute la procédure correspondante sur l'Abonné.  
  
### Pour publier l'exécution d'une procédure stockée  
  
1.  Sur le **Articles** page de l’Assistant Nouvelle Publication ou le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez une procédure stockée.  
  
2.  Cliquez sur **Propriétés de l'article**, puis sur **Définir les propriétés de la procédure stockée en surbrillance**.  
  
3.  Dans la **Propriétés de l’Article - \< Article>** boîte de dialogue, spécifiez une des valeurs suivantes pour le **répliquer** option :  
  
    -   **Exécution de la procédure stockée**  
  
    -   **Exécution de la procédure stockée dans une transaction sérialisée**  
  
         Cette option est recommandée car elle réplique l'exécution de la procédure uniquement si la procédure est exécutée dans le cadre d'une transaction sérialisée. Si la procédure stockée est exécutée hors d'une transaction sérialisée, les modifications apportées aux données des tables publiées sont répliquées en tant que séries d'instructions DML (Data Manipulation Language).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Si vous êtes dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
## Voir aussi  
 [Publication de l'exécution de procédures stockées dans la réplication transactionnelle](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  