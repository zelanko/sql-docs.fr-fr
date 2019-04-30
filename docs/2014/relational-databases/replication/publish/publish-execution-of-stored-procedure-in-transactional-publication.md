---
title: Publier l’exécution d’une procédure stockée dans une Publication transactionnelle (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 07bab8c30c138139dee50b349ac797e5c86fa5c5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63238724"
---
# <a name="publish-the-execution-of-a-stored-procedure-in-a-transactional-publication-sql-server-management-studio"></a>publier l'exécution d'une procédure stockée dans une publication transactionnelle (SQL Server Management Studio)
  Spécifiez que l’exécution d’une procédure stockée (et non sa définition uniquement) doit être publiée dans la boîte de dialogue **Propriétés de l’article - \<Article>**. Cette boîte de dialogue est disponible dans l’Assistant Nouvelle publication et dans la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d’informations sur l’utilisation de l’Assistant et sur l’accès à la boîte de dialogue, consultez [Créer une publication](create-a-publication.md) et [Afficher et modifier les propriétés d’une publication](view-and-modify-publication-properties.md).  
  
 La définition de la procédure (l'instruction CREATE PROCEDURE) est répliquée vers l'Abonné quand l'abonnement est initialisé ; quand la procédure est exécutée sur le serveur de publication, la réplication exécute la procédure correspondante sur l'Abonné.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>Pour publier l'exécution d'une procédure stockée  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication - \<Publication>**, sélectionnez une procédure stockée.  
  
2.  Cliquez sur **Propriétés de l'article**, puis sur **Définir les propriétés de la procédure stockée en surbrillance**.  
  
3.  Dans la boîte de dialogue **Propriétés de l’article - \<Article>**, spécifiez l’une des valeurs suivantes pour l’option **Répliquer** :  
  
    -   **Exécution de la procédure stockée**  
  
    -   **Exécution de la procédure stockée dans une transaction sérialisée**  
  
         Cette option est recommandée car elle réplique l'exécution de la procédure uniquement si la procédure est exécutée dans le cadre d'une transaction sérialisée. Si la procédure stockée est exécutée hors d'une transaction sérialisée, les modifications apportées aux données des tables publiées sont répliquées en tant que séries d'instructions DML (Data Manipulation Language).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Si vous êtes dans la boîte de dialogue **Propriétés de la publication - \<Publication>**, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication de l’exécution de procédures stockées dans la réplication transactionnelle](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
