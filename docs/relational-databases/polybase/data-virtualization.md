---
title: Virtualiser des données externes dans SQL Server 2019 CTP 2.0 | Microsoft Docs
description: ''
author: Abiola
ms.author: aboke
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: polybase
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: dfd4460c51e4aeef8e9faff8479e7edf2678c35f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627317"
---
# <a name="use-the-data-external-table-wizard-with-external-tables"></a>Utiliser l’Assistant Table de données externe avec des tables externes

Un des principaux scénarios pour SQL Server 2019 CTP 2.0 est la possibilité de virtualiser des données.  Ce processus permet aux données de rester à leur emplacement d’origine et de les **virtualiser** dans une instance SQL Server, ce qui vous permet de les interroger comme n’importe quelle autre table dans SQL Server. Vous réduisez ainsi la nécessité de recourir à des processus ETL. Ceci est possible via l’utilisation de connecteurs PolyBase. Pour plus d’informations sur la virtualisation de données, consultez notre document [Bien démarrer avec PolyBase](polybase-guide.md).

## <a name="launch-the-external-table-wizard"></a>Lancer l’Assistant Table externe

Connectez-vous à l’instance master en utilisant l’adresse IP / le numéro de port (31433) obtenus à la fin du script de déploiement. Développez votre nœud **Bases de données** dans l’Explorateur d’objets. Sélectionnez ensuite une des bases de données où vous voulez virtualiser les données à partir d’une instance SQL Server existante. Cliquez avec le bouton droit sur la base de données, puis sélectionnez **Créer une table externe** dans le menu contextuel. Ceci lance l’Assistant Virtualisation de données. Vous pouvez également lancer l’Assistant Virtualisation de données à partir de la palette de commandes en appuyant sur les touches Ctrl+Maj+P (sur Windows) ou Cmd+Maj+P (sur Mac).

![Assistant Virtualisation de données](media/data-virtualization/virtualize-data-wizard.png)
## <a name="select-a-data-source"></a>Sélectionner une source de données

Si vous avez lancé l’Assistant à partir d’une des bases de données, vous pouvez voir que la liste déroulante des destinations est automatiquement renseignée. Vous avez également la possibilité d’entrer ou de changer la base de données de destination sur cet écran. Les types de sources de données externes pris en charge par l’Assistant sont SQL Server et Oracle.

> [!NOTE]
>SQL Server est mis en surbrillance par défaut


![Sélectionner une source de données](media/data-virtualization/select-data-source.png)

Cliquez sur Suivant pour passer à l’étape suivante de l’Assistant, qui définit la clé principale de la base de données.

## <a name="create-database-master-key"></a>Créer une clé principale de base de données

Dans cette étape, vous devez créer une clé principale de base de données. La création de la clé principale est obligatoire, car cela sécurise les informations d’identification utilisées par une source de données externe. Choisissez un mot de passe fort pour votre clé principale. Vous devez aussi sauvegarder la clé principale avec l’instruction BACKUP MASTER KEY et stocker la sauvegarde dans un endroit sécurisé hors site.

![Créer une clé principale de base de données](media/data-virtualization/virtualize-data-master-key.png)

> [!IMPORTANT]
> Si vous disposez déjà d’une clé principale de base de données, les champs d’entrée ne sont pas accessibles et vous pouvez ignorer cette étape. Vous pouvez simplement cliquer sur « Suivant » pour passer à la page suivante de l’Assistant.

> [!NOTE]
> Si vous ne choisissez pas un mot de passe fort, l’Assistant passe directement à la dernière étape. Il s’agit d’un problème connu qui sera corrigé dans la version à venir, avec un processus plus intuitif.

## <a name="enter-the-external-data-source-credentials"></a>Entrer les informations d’identification de la source de données externe

Dans cette étape, entrez les détails de votre source de données externe et des informations d’identification. Cette étape crée un objet de source de données externe, puis utilise les informations d’identification pour que l’objet de base de données se connecte à la source de données. Spécifiez un nom pour la source de données externe (par exemple « Test ») et les détails de la connexion SQL Server à la source de données externe : le nom du serveur et le nom de la base de données où vous voulez que votre source de données externe soit créée sur ce serveur.

L’étape suivante consiste à configurer les informations d’identification. Spécifiez un nom pour les informations d’identification : il s’agit du nom des informations d’identification limitées à la base de données, utilisées pour stocker de façon sécurisée les informations de connexion pour la source de données externe que vous créez (par exemple « TestCred »). Spécifiez aussi le nom d’utilisateur et le mot de passe pour se connecter à la source de données.

![Informations d’identification de la source de données externe](media/data-virtualization/data-source-credentials.png)

## <a name="external-data-table-mapping"></a>Mappage de tables de données externe

Dans la fenêtre suivante, vous pouvez sélectionner les tables pour lesquelles vous voulez créer des vues externes. La sélection des bases de données parentes inclut également toutes les tables enfants. Quand les tables sont sélectionnées, vous pouvez voir un tableau des mappages sur le côté droit. Vous pouvez apporter ici des modifications de « type » ou changer le nom de la table externe sélectionnée elle-même.

![Informations d’identification de la source de données externe](media/data-virtualization/data-table-mapping.png)

> [!NOTE]
>Le fait de double-cliquer sur une autre table sélectionnée change la vue du mappage.

> [!IMPORTANT]
>Le type « photo »n’est pas encore pris en charge par l’outil Table externe. Le fait de créer une vue externe contenant un type « photo » provoque une erreur après la création de la table. La table est néanmoins créée.

## <a name="summary"></a>Résumé

Cette étape fournit un récapitulatif de vos sélections. Il indique le nom des informations d’identification limitées à la base de données et les objets de source de données externe qui seront créés dans la base de données de destination. Dans cette étape, vous pouvez choisir **Générer un script** avec la syntaxe en T-SQL nécessaire pour créer la source de données externe ou **Créer**, qui crée l’objet de source de données externe.

![Écran Récapitulatif](media/data-virtualization/virtualize-data-summary.png)

Si vous cliquez sur « Créer », vous pouvez voir l’objet de source de données externe créé dans la base de données de destination.

![Sources de données externes](media/data-virtualization/external-data-sources.png)

Si vous cliquez sur **Générer un script**, vous voyez que la requête T-SQL est générée pour créer l’objet de source de données externe.

![Générer un script](media/data-virtualization/generated-script.png)

> [!NOTE]
> L’option Générer un script doit normalement être visible seulement dans la dernière page de l’Assistant. Actuellement, elle apparaît dans toutes les pages.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server Big Data Cluster et les scénarios associés, consultez [Qu’est-ce que SQL Server Big Data Cluster ?](../../big-data-cluster/big-data-cluster-overview.md).
