---
title: 'Leçon 1 : Publication de données à l’aide de la réplication transactionnelle | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 9c55aa3c-4664-41fc-943f-e817c31aad5e
author: rothja
ms.author: jroth
ms.openlocfilehash: ff715b51a7fa84a462d1439e78627d648e20472d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065956"
---
# <a name="lesson-1-publishing-data-using-transactional-replication"></a>Leçon 1 : publication de données à l'aide de la réplication transactionnelle
   Dans cette leçon, vous créez une publication transactionnelle en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour publier un sous-ensemble filtré de la table **Product** de l’exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Vous allez aussi ajouter à la liste d'accès à la publication le compte de connexion SQL Server utilisée par l'Agent de distribution. Avant de commencer ce didacticiel, vous devez avoir terminé le didacticiel précédent, [Préparation du serveur à la réplication](tutorial-preparing-the-server-for-replication.md).  
  
### <a name="to-create-a-publication-and-define-articles"></a>Pour créer une publication et définir des articles  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , cliquez avec le bouton droit sur le dossier **Publications locales** , puis cliquez sur **Nouvelle publication**.  
  
     L'Assistant Configuration de la publication démarre.  
  
3.  Dans la page Base de données de publication, sélectionnez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], puis cliquez sur **Suivant**.  
  
4.  Dans la page Type de publication, sélectionnez **Publication transactionnelle**, puis cliquez sur **Suivant**.  
  
5.  Dans la page Articles, développez le nœud **Tables** , cochez la case **Product** , puis développez **Product** et décochez les cases **ListPrice** et **StandardCost** . Cliquez sur **Suivant**.  
  
6.  Dans la page Filtrer les lignes de la table, cliquez sur **Ajouter**.  
  
7.  Dans la boîte de dialogue **Ajouter un filtre** , cliquez sur la colonne **SafetyStockLevel** , cliquez sur la flèche droite pour ajouter la colonne à la clause WHERE de la requête de filtre et modifiez la clause WHERE comme suit :  
  
    ```  
    WHERE [SafetyStockLevel] < 500  
    ```  
  
8.  Cliquez sur **OK**, puis cliquez sur **Suivant**.  
  
9. Cochez la case **Créer un instantané immédiatement et garder ce dernier disponible pour l’initialisation des abonnements** et cliquez sur **Suivant**.  
  
10. Dans la page Sécurité de l’agent, décochez la case **Utiliser les paramètres de sécurité de l’Agent d’instantané** .  
  
11. Cliquez sur **paramètres de sécurité** pour la agent d’instantané, entrez \<_Machine_Name> _**\ repl_snapshot** dans la zone **compte de processus** , fournissez le mot de passe de ce compte, puis cliquez sur **OK**.  
  
12. Répétez l’étape précédente pour définir repl_logreader comme compte de processus de l’Agent de lecture du journal, puis cliquez sur **Terminer**.  
  
13. Dans la page Terminer l’Assistant, entrez **AdvWorksProductTrans** dans la zone **Nom de la publication** , puis cliquez sur **Terminer**.  
  
14. Une fois la publication créée, cliquez sur **Fermer** pour terminer l’Assistant.  
  
### <a name="to-view-the-status-of-snapshot-generation"></a>Pour afficher l'état d'une génération d'instantané  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier **Publications locales** , cliquez avec le bouton droit sur **AdvWorksProductTrans**, puis cliquez sur **Afficher l’état de l’Agent d’instantané**.  
  
3.  L'état en cours du travail de l'Agent d'instantané pour la publication s'affiche. Vérifiez que le travail d'instantané a bien réussi avant de passer à la leçon suivante.  
  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a>Pour ajouter la connexion de l'Agent de distribution à la liste d'accès à la publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier **Publications locales** , cliquez avec le bouton droit sur **AdvWorksProductTrans**, puis cliquez sur **Propriétés**.  
  
     La boîte de dialogue **Propriétés de la publication** s’affiche.  
  
3.  Sélectionnez la page **Liste d’accès à la publication** , puis cliquez sur **Ajouter**.  
  
4.  \Dans la boîte de dialogue **Ajouter un accès à une publication**, sélectionnez _nom_ordinateur>_**\repl_distribution** et cliquez sur **OK**. Cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez créé avec succès la publication transactionnelle. Ensuite, vous allez créer l'abonnement à cette publication. Consultez [Leçon 2 : Création d’un abonnement à la publication transactionnelle](lesson-2-creating-a-subscription-to-the-transactional-publication.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer les données publiées](publish/filter-published-data.md)   
 [Définir un article](publish/define-an-article.md)   
 [Créer et appliquer un instantané](create-and-apply-the-snapshot.md)  
  
  
