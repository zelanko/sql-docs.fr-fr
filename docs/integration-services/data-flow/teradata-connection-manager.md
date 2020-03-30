---
title: Utiliser le gestionnaire de connexions Teradata | Microsoft Docs
ms.custom: ''
ms.date: 11/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d520f83f515694bd8852ce11ea13fce7f3213596
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "75245121"
---
# <a name="use-the-teradata-connection-manager"></a>Utiliser le gestionnaire de connexions Teradata

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Avec le gestionnaire de connexions Teradata, vous pouvez permettre à un package d’extraire des données de bases de données Teradata et de charger des données dans ces bases.

Vous définissez la propriété `ConnectionManagerType` du gestionnaire de connexions Teradata sur *TERADATA*.

## <a name="configure-the-teradata-connection-manager"></a>Configurer le gestionnaire de connexions Teradata

Les modifications apportées à la configuration du gestionnaire de connexions sont résolues par Integration Services au moment de l’exécution. Pour ajouter une connexion à une source de données Teradata, renseignez le volet **Éditeur du gestionnaire de connexions Teradata**.

![Volet Éditeur du gestionnaire de connexions Teradata](media/teradata-connection-manager.png)

1. Dans la zone **Nom**, entrez un nom pour la connexion. Le nom par défaut est **Gestionnaire de connexions Teradata**.

1. (Facultatif) Dans la zone **Description**, entrez une description de la connexion.

1. Dans la zone **Nom du serveur**, entrez le nom du serveur Teradata auquel vous connecter.

1. Sous **Authentification**, effectuez l’une des opérations suivantes :

   - Pour utiliser l’authentification Windows, sélectionnez **Utiliser l’authentification Windows**.
   - Pour utiliser l’authentification de base de données Teradata, sélectionnez **Utiliser l’authentification Teradata**, puis entrez les informations d’identification suivantes pour ce type d’authentification :
     - Dans la zone **Mécanisme**, indiquez le mécanisme de vérification de sécurité que vous souhaitez utiliser. Les valeurs de mécanisme valides sont notamment TD1, TD2, LDAP, KRB5, KRB5C, NTLM et NTLMC.
     - Dans la zone **Paramètre**, entrez les types de paramètres requis pour le mécanisme de vérification de sécurité que vous avez spécifié.
     - Dans la zone **Nom d’utilisateur**, entrez le nom d’utilisateur que vous utilisez pour vous connecter à la base de données Teradata.  
     - Dans la zone **Mot de passe**, entrez le mot de passe de base données Teradata de l’utilisateur.

1. (Facultatif) Dans la liste déroulante **Base de données par défaut**, sélectionnez la base de données Teradata auprès de laquelle établir la connexion. Si cette autorisation d’accès à la base de données est incorrecte, une erreur s’affiche. Vous pouvez alors entrer manuellement le nom de la base de données.

1. (Facultatif) Dans la zone **Compte**, entrez le nom du compte associé au nom d’utilisateur. Si cette valeur est vide, le compte du propriétaire immédiat de la base de données est utilisé.
1. Sélectionnez **OK**.

## <a name="custom-property"></a>Propriété personnalisée

La propriété personnalisée `UseUTF8CharSet` spécifie si le jeu de caractères UTF-8 est utilisé. La valeur par défaut est *True*.

Pour définir la propriété :

1. Ouvrez SQL Server Data Tools (SSDT).
1. Dans la zone **Gestionnaires de connexions**, cliquez avec le bouton droit sur **Gestionnaire de connexions Teradata**, puis sélectionnez **Propriétés**.
1. Dans le volet **Propriétés**, sélectionnez `UseUTF8CharSet`Vrai*ou*Faux*pour la propriété*.

## <a name="troubleshoot-the-teradata-connection-manager"></a>Résoudre les problèmes liés au gestionnaire de connexions Teradata

Pour journaliser les appels du gestionnaire de connexions Teradata au pilote ODBC (Open Database Connectivity) Teradata, activez le traçage ODBC Windows dans l’Administrateur de sources de données ODBC Windows.

## <a name="next-steps"></a>Étapes suivantes

- Configurez la [source Teradata](teradata-source.md).
- Configurez la [destination Teradata](teradata-destination.md).
- Si vous avez des questions, rendez-vous sur [Tech Community](https://aka.ms/AA5u35j).
