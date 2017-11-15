---
title: "Publier l’exécution d’une procédure stockée dans une publication transactionnelle | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a709463393f37dd3d6ac3af64f62fe70a8556cad
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="publish-execution-of-stored-procedure-in-transactional-publication"></a>Publier l’exécution d’une procédure stockée dans une publication transactionnelle
  Spécifiez que l’exécution d’une procédure stockée (et non sa définition uniquement) doit être publiée dans la boîte de dialogue **Propriétés de l’article - \<Article>**. Cette boîte de dialogue est disponible dans l’Assistant Nouvelle publication et dans la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d’informations sur l’utilisation de l’Assistant et sur l’accès à la boîte de dialogue, consultez [Créer une publication](../../../relational-databases/replication/publish/create-a-publication.md) et [Afficher et modifier les propriétés d’une publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 La définition de la procédure (l'instruction CREATE PROCEDURE) est répliquée vers l'Abonné quand l'abonnement est initialisé ; quand la procédure est exécutée sur le serveur de publication, la réplication exécute la procédure correspondante sur l'Abonné.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>Pour publier l'exécution d'une procédure stockée  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication - \<Publication>**, sélectionnez une procédure stockée.  
  
2.  Cliquez sur **Propriétés de l'article**, puis sur **Définir les propriétés de la procédure stockée en surbrillance**.  
  
3.  Dans la boîte de dialogue **Propriétés de l’article - \<Article>**, spécifiez l’une des valeurs suivantes pour l’option **Répliquer** :  
  
    -   **Exécution de la procédure stockée**  
  
    -   **Exécution de la procédure stockée dans une transaction sérialisée**  
  
         Cette option est recommandée car elle réplique l'exécution de la procédure uniquement si la procédure est exécutée dans le cadre d'une transaction sérialisée. Si la procédure stockée est exécutée hors d'une transaction sérialisée, les modifications apportées aux données des tables publiées sont répliquées en tant que séries d'instructions DML (Data Manipulation Language).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Si vous êtes dans la boîte de dialogue **Propriétés de la publication - \<Publication>**, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication de l’exécution de procédures stockées dans la réplication transactionnelle](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
