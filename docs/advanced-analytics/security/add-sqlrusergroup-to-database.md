---
title: Ajouter SQLRUserGroup comme un utilisateur de base de données (SQL Server Machine Learning) | Microsoft Docs
description: Pour les connexions de bouclage à l’aide de l’authentification implicite, ajouter SQLRUserGroup comme un utilisateur de base de données afin qu’un compte de travail permettre se connecter au serveur, pour la conversion d’identité à l’utilisateur appelant.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4685288eb383c486556efba1eb4861ca9d708c0f
ms.sourcegitcommit: 13d98701ecd681f0bce9ca5c6456e593dfd1c471
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49419084"
---
# <a name="add-sqlrusergroup-as-a-database-user"></a>Ajouter SQLRUserGroup comme utilisateur de base de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Créez une connexion de base de données pour [SQLRUserGroup](../concepts/security.md#sqlrusergroup) lorsqu’un [connexion de retour de boucle](../../advanced-analytics/concepts/security.md#implied-authentication) dans votre script spécifie une *connexion approuvée*et l’identité utilisée pour exécuter un objet contient votre code est un compte d’utilisateur Windows.

Approuvé les connexions sont celles ayant `Trusted_Connection=True` dans la chaîne de connexion. Lorsque SQL Server reçoit une requête spécifiant une connexion approuvée, il vérifie si l’identité de l’utilisateur Windows actuel dispose d’une connexion. Pour l’exécution sous un compte de travail des processus externes (tels que MSSQLSERVER01 de **SQLRUserGroup**), la demande échoue, car ces comptes n’ont pas un compte de connexion par défaut.

Vous pouvez contourner l’erreur de connexion en donnant **SQLServerRUserGroup** une connexion SQL Server. Pour plus d’informations sur les identités et des processus externes, consultez [vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité](../concepts/security.md).

> [!Note]
>  Assurez-vous que l’option **SQLRUserGroup** dispose des autorisations « Autoriser la connexion localement ». Par défaut, ce droit est attribué à tous les nouveaux utilisateurs locaux, mais dans certaines organisations, les stratégies de groupe plus strictes peuvent désactiver ce droit.

## <a name="create-a-login"></a>Créer un compte de connexion

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, développez **Sécurité**, cliquez avec le bouton droit sur **Connexions**, puis sélectionnez **Nouvelle connexion**.

2. Dans le **nouvelle connexion** boîte de dialogue, sélectionnez **recherche**. (Ne tapez pas quoi que ce soit dans la zone encore.)
    
     ![Cliquez sur Rechercher pour ajouter le nouveau compte de connexion pour l’apprentissage](media/implied-auth-login1.png "cliquez sur Rechercher pour ajouter nouvelle connexion pour l’apprentissage")

3. Dans le **sélectionner utilisateur ou groupe** , cliquez sur le **Types d’objet** bouton.

     ![Rechercher des types d’objets à ajouter nouvelle connexion pour l’apprentissage](media/implied-auth-login2.png "rechercher des types d’objets à ajouter nouvelle connexion pour l’apprentissage")

4. Dans le **Types d’objets** boîte de dialogue, sélectionnez **groupes**. Désactivez toutes les autres cases à cocher.

     ![Sélectionnez les groupes dans la boîte de dialogue Types d’objets](media/implied-auth-login3.png "sélectionner des groupes dans la boîte de dialogue Types d’objets")

4. Cliquez sur **avancé**, vérifiez que l’emplacement auquel rechercher est l’ordinateur actuel, puis cliquez sur **Rechercher maintenant**.

     ![Cliquez sur Rechercher pour obtenir la liste des groupes](media/implied-auth-login4.png "cliquez sur Rechercher pour obtenir la liste des groupes")

5. Faites défiler la liste des comptes de groupe sur le serveur jusqu'à ce que vous trouviez une commençant par `SQLRUserGroup`.
    
    + Le nom du groupe associé avec le service Launchpad de le _instance par défaut_ est toujours **SQLRUserGroup**, indépendamment de si vous avez installé R ou Python. Sélectionnez ce compte pour l’instance par défaut uniquement.
    + Si vous utilisez un _instance nommée_, le nom d’instance est ajouté au nom du nom de groupe de travail par défaut, `SQLRUserGroup`. Par exemple, si votre instance est nommée « MLTEST », le nom du groupe utilisateur par défaut pour cette instance serait **SQLRUserGroupMLTest**.
 
 ![Exemple de groupes sur serveur](media/implied-auth-login5.png "exemples de groupes sur le serveur")
   
5. Cliquez sur **OK** pour fermer la boîte de dialogue Recherche avancée.

    > [!IMPORTANT]
    > Veillez à ce que vous avez sélectionné le compte approprié pour l’instance. Chaque instance peut utiliser uniquement dans son propre service Launchpad et le groupe créé pour ce service. Instances ne peuvent pas partager un compte de service ou de travail Launchpad.

6. Cliquez sur **OK** pour fermer la **sélectionner utilisateur ou groupe** boîte de dialogue.

7. Dans le **nouvelle connexion** boîte de dialogue, cliquez sur **OK**. Par défaut, la connexion est affectée au rôle **public** et est autorisée à se connecter au moteur de base de données.

## <a name="next-steps"></a>Étapes suivantes

+ [Vue d’ensemble de la sécurité](../concepts/security.md)
+ [Infrastructure d’extensibilité](../concepts/extensibility-framework.md)