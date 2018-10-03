---
title: Spécifier qu’un article de table de fusion est en téléchargement seul | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], download-only articles
- articles [SQL Server replication], download-only
- download-only articles
ms.assetid: 14839cec-6dbf-49c2-aa27-56847b09b4db
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 694644e51b134c0063c0162b163b83e94e53354a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48144999"
---
# <a name="specify-that-a-merge-table-article-is-download-only"></a>Spécifier qu'un article de table de fusion est en téléchargement seul
  Cette rubrique explique comment définir un article de table de fusion en téléchargement seul dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Les articles en téléchargement uniquement sont conçus pour les applications dont les données ne sont pas mises à jour au niveau des Abonnés. Pour plus d’informations, consultez [Optimiser les performances de la réplication de fusion avec les articles en téléchargement seul](../merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
-   **Pour spécifier qu'un article de table de fusion est en téléchargement seul à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si vous spécifiez qu'un article est en téléchargement seul après l'initialisation des abonnements, tous les abonnements client qui ont reçu l'aticle doivent être réinitialisés. Les abonnements serveur n'ont pas besoin d'être réinitialisés. Pour plus d’informations sur les effets des modifications de propriétés, consultez [Changer des propriétés de publication et d’article](change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifiez qu’un article est en téléchargement seul dans la page **Articles** de l’Assistant Nouvelle publication ou sous l’onglet **Propriétés** de la boîte de dialogue **Propriétés de l’article - \<Article>**. Cette boîte de dialogue est disponible dans l’Assistant Nouvelle publication et dans la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d’informations sur l’utilisation de l’Assistant et sur l’accès à la boîte de dialogue, consultez [Créer une publication](create-a-publication.md) et [Afficher et modifier les propriétés d’une publication](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-that-an-article-is-download-only-on-the-articles-page"></a>Pour spécifier qu'un article est en téléchargement seul dans la page Articles  
  
-   Dans la page **Articles** de l'Assistant Nouvelle publication, sélectionnez une table, puis activez la case à cocher **La table sélectionnée est en téléchargement seul**.  
  
#### <a name="to-specify-that-an-article-is-download-only-on-the-properties-tab-of-the-article-properties---article-dialog-box"></a>Pour spécifier qu’un article est en téléchargement seul sous l’onglet Propriétés de la boîte de dialogue Propriétés de l’article - \<Article>  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication - \<Publication>**, sélectionnez une table, puis cliquez sur **Propriétés de l’article**.  
  
2.  Cliquez sur **Définir les propriétés de l'article de la table en surbrillance** ou **Définir les propriétés de tous les articles de la table**.  
  
3.  Dans la section **Objet de destination** de l’onglet **Propriétés** de la boîte de dialogue **Propriétés de l’article - \<Article>**, spécifiez l’une des valeurs suivantes pour **Direction de la synchronisation** :  
  
    -   **Téléchargement seul pour l'Abonné, interdire les modifications de l'Abonné**  
  
    -   **Téléchargement seul pour l'Abonné, autoriser les modifications de l'Abonné**  
  
4.  Si vous êtes dans la boîte de dialogue **Propriétés de la publication - \<Publication>**, cliquez sur **OK** pour enregistrer et fermer la boîte de dialogue.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-specify-that-a-new-merge-table-article-is-download-only"></a>Pour spécifier qu'une nouvelle table de fusion est en téléchargement uniquement  
  
1.  Exécutez [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), en affectant la valeur **1** ou de **2** au paramètre **@subscriber_upload_options**. Ces chiffres correspondent aux comportements suivants :  
  
    -   **0** - aucune restriction (valeur par défaut). Les modifications sur l'abonné sont téléchargées par le serveur de publication.  
  
    -   **1** -  modifications autorisées au niveau de l'Abonné, mais elles ne sont pas téléchargées sur le serveur de publication.  
  
    -   **2** - modifications interdites au niveau de l'Abonné.  
  
        > [!NOTE]  
        >  Si la table source d'un article est déjà publiée dans une autre publication, la valeur de **@subscriber_upload_options** doit être la même pour les deux articles.  
  
#### <a name="to-modify-an-existing-merge-table-article-to-be-download-only"></a>Pour modifier un article de table fusion existant en article en téléchargement uniquement  
  
1.  Pour déterminer si un article est en téléchargement uniquement, exécutez [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql). Notez la valeur de **upload_options** pour l'article dans le jeu de résultats.  
  
2.  Si la valeur retournée à l'étape 1 est **0**, exécutez [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), en affectant la valeur **subscriber_upload_options** à **@property**, la valeur **1** à **@force_invalidate_snapshot** et **@force_reinit_subscription**, et la valeur **1** ou de **2** à **@value**, qui correspondent aux comportements suivants :  
  
    -   **1** -  modifications autorisées au niveau de l'Abonné, mais elles ne sont pas téléchargées sur le serveur de publication.  
  
    -   **2** - modifications interdites au niveau de l'Abonné.  
  
        > [!NOTE]  
        >  Si la table source d'un article est déjà publiée dans une autre publication, les deux articles doivent être en téléchargement uniquement ou ne pas l'être.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimiser les performances de la réplication de fusion avec les articles en téléchargement seul](../merge/optimize-merge-replication-performance-with-download-only-articles.md)   
 [Define an Article](define-an-article.md)   
 [Afficher et modifier les propriétés d’un article](view-and-modify-article-properties.md)  
  
  
