---
title: Créer un nom de connexion pour SQLRUserGroup
description: Pour les connexions de bouclage utilisant l’authentification implicite, créez une connexion dans SQL Server pour SQLRUserGroup, afin qu’un compte de travail puisse se connecter au serveur, pour la conversion d’identité vers l’utilisateur appelant.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/25/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: f86bedc3cfd92272b500d5d3edd701b6ca51d38b
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469989"
---
# <a name="create-a-login-for-sqlrusergroup"></a>Créer un nom de connexion pour SQLRUserGroup
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Créer une connexion [dans SQL Server](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/create-a-login) pour [SQLRUserGroup](../concepts/security.md#sqlrusergroup) quand une [connexion de retour de boucle](../../advanced-analytics/concepts/security.md#implied-authentication) dans votre script spécifie une *connexion approuvée*, et que l’identité utilisée pour exécuter un objet contient votre code est un compte d’utilisateur Windows.

Les connexions approuvées sont `Trusted_Connection=True` celles qui ont dans la chaîne de connexion. Lorsque SQL Server reçoit une demande spécifiant une connexion approuvée, il vérifie si l’identité de l’utilisateur Windows actuel dispose d’une connexion. Pour les processus externes s’exécutant en tant que compte de travail (par exemple, MSSQLSERVER01 à partir de **SQLRUserGroup**), la demande échoue, car ces comptes n’ont pas de connexion par défaut.

Vous pouvez contourner l’erreur de connexion en créant une connexion pour **SQLServerRUserGroup**. Pour plus d’informations sur les identités et les processus externes, consultez [vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité](../concepts/security.md).

> [!Note]
> Assurez-vous que **SQLRUserGroup** dispose des autorisations «permettre l’ouverture d’une session locale». Par défaut, ce droit est accordé à tous les nouveaux utilisateurs locaux, mais certaines organisations appliquent des stratégies de groupe plus strictes.

## <a name="create-a-login"></a>Créer un compte de connexion

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, développez **Sécurité**, cliquez avec le bouton droit sur **Connexions**, puis sélectionnez **Nouvelle connexion**.

2. Dans la boîte de dialogue **nouvelle connexion** , sélectionnez **Rechercher**. (Ne tapez rien dans la zone.)
    
     ![Cliquez sur Rechercher pour ajouter une nouvelle connexion pour machine learning](media/implied-auth-login1.png "Cliquez sur Rechercher pour ajouter une nouvelle connexion pour machine learning")

3. Dans la zone **Sélectionner un utilisateur ou un groupe** , cliquez sur le bouton types d' **objets** .

     ![Rechercher des types d’objet pour ajouter une nouvelle connexion pour machine learning](media/implied-auth-login2.png "Rechercher des types d’objet pour ajouter une nouvelle connexion pour machine learning")

4. Dans la boîte de dialogue **types d’objets** , sélectionnez **groupes**. Désactivez toutes les autres cases à cocher.

     ![Boîte de dialogue Sélectionner des groupes dans les types d’objets](media/implied-auth-login3.png "Boîte de dialogue Sélectionner des groupes dans les types d’objets")

4. Cliquez sur **avancé**, vérifiez que l’emplacement de recherche est l’ordinateur actuel, puis cliquez sur **Rechercher**.

     ![Cliquez sur Rechercher maintenant pour obtenir la liste des groupes](media/implied-auth-login4.png "Cliquez sur Rechercher maintenant pour obtenir la liste des groupes")

5. Faites défiler la liste des comptes de groupe sur le serveur jusqu’à ce `SQLRUserGroup`que vous en trouviez un à partir de.
    
    + Le nom du groupe associé au service Launchpad pour l' _instance par défaut_ est toujours **SQLRUserGroup**, que vous ayez installé R ou python ou les deux. Sélectionnez ce compte pour l’instance par défaut uniquement.
    + Si vous utilisez une _instance nommée_, le nom de l’instance est ajouté au nom du groupe de travail par défaut, `SQLRUserGroup`. Par exemple, si votre instance est nommée «MLTEST», le nom de groupe d’utilisateurs par défaut pour cette instance serait **SQLRUserGroupMLTest**.
 
    ![Exemple de groupes sur le serveur](media/implied-auth-login5.png "Exemple de groupes sur le serveur")
   
5. Cliquez sur **OK** pour fermer la boîte de dialogue Recherche avancée.

    > [!IMPORTANT]
    > Vérifiez que vous avez sélectionné le compte approprié pour l’instance. Chaque instance peut utiliser uniquement son propre service Launchpad et le groupe créé pour ce service. Les instances ne peuvent pas partager un service Launchpad ou des comptes Worker.

6. Cliquez sur **OK** une fois de plus pour fermer la boîte de dialogue **Sélectionner un utilisateur ou un groupe** .

7. Dans la boîte de dialogue **nouvelle connexion** , cliquez sur **OK**. Par défaut, la connexion est affectée au rôle **public** et est autorisée à se connecter au moteur de base de données.

## <a name="next-steps"></a>Étapes suivantes

+ [Vue d’ensemble de la sécurité](../concepts/security.md)
+ [Infrastructure d’extensibilité](../concepts/extensibility-framework.md)
