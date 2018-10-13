---
title: Ajouter SQLRUserGroup comme un utilisateur de base de données (SQL Server Machine Learning) | Microsoft Docs
description: Comment ajouter SQLRUserGroup comme un utilisateur de base de données pour SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: fc5294453def64d13cc43a74a8a5fb299c3e23e3
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100320"
---
# <a name="add-sqlrusergroup-as-a-database-user"></a>Ajouter SQLRUserGroup comme utilisateur de base de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Créez une connexion de base de données pour le [SQLRUserGroup](../concepts/security.md#sqlrusergroup) pour autoriser les connexions approuvées provenant de scripts R et Python lorsque la cible est données ou des opérations sur l’instance de SQL Server. 

Pour les scripts contenant des chaînes de connexion avec les connexions SQL Server ou un nom d’utilisateur spécifié et le mot de passe, la création d’une connexion n’est pas nécessaire.

## <a name="when-a-login-is-required"></a>Quand une connexion est requise

Si le script R ou Python inclut une chaîne de connexion spécifiant une connexion approuvée (par exemple, « Trusted_Connection = True »), une configuration supplémentaire est nécessaire pour la présentation de l’identité de l’utilisateur à SQL Server. Pour les processus externes en cours d’exécution sous un **SQLRUserGroup** compte de travail, tels que MSSQLSERVER01, l’utilisateur approuvé est présentée sous l’identité du travail. Étant donné que cette identité dispose d’aucun droit de connexion à SQL Server, approuvé connexions échouent sauf si vous ajoutez **SQLRUserGroup** en tant qu’un utilisateur de base de données. Pour plus d’informations, consultez [ *l’authentification implicite*](../../advanced-analytics/concepts/security.md#implied-authentication).

Rappelez-vous que Launchpad conserve un mappage de l’utilisateur d’origine qui a appelé le script et le compte de travail qui exécute le processus. Une fois la connexion approuvée réussi pour le compte de travail, l’identité de l’utilisateur appelant d’origine adopte et est utilisée pour récupérer les données. Vous n’avez pas besoin accorder des autorisations db_datareader à **SQLRUserGroup**.

> [!Note]
>  Assurez-vous que l’option **SQLRUserGroup** dispose des autorisations « Autoriser la connexion localement ». Par défaut, ce droit est attribué à tous les nouveaux utilisateurs locaux, mais dans certaines organisations des stratégies de groupe plus strictes peuvent être appliquées.

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
    + Si vous utilisez un _instance nommée_, le nom d’instance est ajouté au nom du nom de groupe de travail par défaut, `SQLRUserGroup`. Par conséquent, si votre instance est nommée « MLTEST », le nom du groupe utilisateur par défaut pour cette instance serait **SQLRUserGroupMLTest**.
 
     ![Exemple de groupes sur serveur](media/implied-auth-login5.png "exemples de groupes sur le serveur")
   
5. Cliquez sur **OK** pour fermer la boîte de dialogue Recherche avancée.

    > [!IMPORTANT]
    > Veillez à ce que vous avez sélectionné le compte approprié pour l’instance. Chaque instance peut utiliser uniquement dans son propre service Launchpad et le groupe créé pour ce service. Instances ne peuvent pas partager un compte de service ou de travail Launchpad.

6. Cliquez sur **OK** pour fermer la **sélectionner utilisateur ou groupe** boîte de dialogue.

7. Dans le **nouvelle connexion** boîte de dialogue, cliquez sur **OK**. Par défaut, la connexion est affectée au rôle **public** et est autorisée à se connecter au moteur de base de données.