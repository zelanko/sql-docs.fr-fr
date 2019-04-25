---
title: Migrer le schéma HR Oracle vers SQL Server sur Linux | Microsoft Docs
description: Convertir l’exemple de schéma Oracle vers SQL Server sur Linux
author: shamikg
ms.author: shamikg
manager: v-thobro
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: ''
ms.technology: ssma
ms.openlocfilehash: 312797b2b883f764fc65588e72cd67d7227e327a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62629788"
---
# <a name="migrate-an-oracle-schema-to-sql-server-2017-on-linux-with-the-sql-server-migration-assistant"></a>Migrer un schéma d’Oracle vers SQL Server 2017 sur Linux avec l’Assistant Migration SQL Server

Ce didacticiel utilise SQL Server Migration Assistant (SSMA) pour Oracle sur Windows pour convertir l’exemple Oracle **HR** schéma à [SQL Server 2017 sur Linux](../../linux/sql-server-linux-overview.md).

> [!div class="checklist"]
> * Télécharger et installer SSMA sur Windows
> * Créer un projet SSMA pour gérer la migration
> * Connexion à Oracle
> * Exécuter un rapport de migration
> * Convertir l’exemple de schéma HR
> * Migrer les données

## <a name="prerequisites"></a>Prérequis

- Une instance d’Oracle 12C (12.2.0.1.0) avec le schéma **HR** installé
- Une instance de travail de SQL Server sur Linux

> [!NOTE]
> Les mêmes étapes peuvent être utilisées pour cibler SQL Server sur Windows, mais vous devez sélectionner Windows dans le paramètre **Migrer vers** du projet.

## <a name="download-and-install-ssma-for-oracle"></a>Télécharger et installer SSMA pour Oracle

Il existe plusieurs éditions de SQL Server Migration Assistant disponibles, en fonction de votre base de données source.  Télécharger la version actuelle de [SQL Server Migration Assistant pour Oracle](https://aka.ms/ssmafororacle) et installez-le à l’aide des instructions figurant sur la page de téléchargement.

> [!NOTE]
> À ce stade, le **SSMA pour Oracle Extension Pack** n’est pas pris en charge sur Linux, mais il n’est pas nécessaire pour ce didacticiel.

## <a name="create-and-set-up-project"></a>Créer et de projet d’installation

Utilisez les étapes suivantes pour créer un nouveau projet SSMA :

1. Ouvrez SSMA pour Oracle et choisissez **Nouveau projet** à partir du menu **fichier**.

1. Nommez le projet.

1. Choisissez « SQL Server 2017 (Linux) - version préliminaire » dans le champ **Migrer vers**.

SSMA pour Oracle n’utilise pas les exemples de schémas Oracle par défaut. Pour activer le schéma HR, procédez comme suit :

1. Dans SSMA, sélectionnez le menu **Outils**.

1. Sélectionnez **Paramètres de projet par défaut**, puis choisissez **Chargement des objets système**.

1. Assurez-vous que **HR** est activée, puis choisissez **OK**.

## <a name="connect-to-oracle"></a>Connexion à Oracle

Ensuite, connectez SSMA à Oracle.

1. Dans la barre d’outils, cliquez sur **Se connecter à Oracle**.

1. Entrez le nom du serveur, un port, un SID Oracle, un nom d’utilisateur et un mot de passe.

   ![Connexion à Oracle](./media/sql-server-linux-convert-from-oracle/ConnectToOracle.png)

1. Puis cliquez sur **Connexion**. Dans quelques instants, SSMA pour Oracle se connecte à votre base de données et lit ses métadonnées.

## <a name="create-a-report"></a>Créer un rapport

Utilisez les étapes suivantes pour générer un rapport de migration.

1. Dans le **Explorateur de métadonnées d’Oracle**, développez votre nœud de serveur.

1. Développez **schémas**, avec le bouton droit **HR**, puis sélectionnez **créer un rapport**.

   ![Explorateur de métadonnées d’Oracle créer des rapports](./media/sql-server-linux-convert-from-oracle/CreateReport.png)

1. Une nouvelle fenêtre de navigateur s’ouvre avec un rapport qui répertorie tous les avertissements et erreurs associés à la conversion.

   > [!NOTE]
   > Vous n’avez rien à faire avec cette liste pour ce didacticiel. Si vous effectuez ces étapes pour votre propre base de données Oracle, vous devez examiner le rapport pour traiter tous les problèmes de conversion important pour votre base de données.

   ![Exemple de rapport de Migration](./media/sql-server-linux-convert-from-oracle/SSMAReport.png)

## <a name="connect-to-sql-server"></a>Se connecter à SQL Server

Ensuite, choisissez **se connecter à SQL Server** et entrez les informations de connexion appropriées.  Si vous utilisez un nom de base de données qui n’existe pas encore, SSMA pour Oracle le crée pour vous.

![Se connecter à SQL Server](./media/sql-server-linux-convert-from-oracle/ConnectToSQLServer.png)

## <a name="convert-schema"></a>Convertir le schéma

Avec le bouton droit sur **HR** dans **Explorateur de métadonnées d’Oracle**, puis choisissez Convertir le schéma.

![Convertir le schéma](./media/sql-server-linux-convert-from-oracle/ConvertSchema.png)

## <a name="synchronize-database"></a>Synchroniser la base de données

Ensuite, synchronisez votre base de données.

1. Une fois la conversion terminée, utilisez l’**Explorateur de métadonnées SQL Server** pour accéder à la base de données que vous avez créé à l’étape précédente.

1. Avec le bouton droit sur votre base de données, sélectionnez **Synchroniser avec la base de données**, puis cliquez sur OK.

   ![Synchroniser avec la base de données](./media/sql-server-linux-convert-from-oracle/SynchronizeWithDatabase.png)

## <a name="migrate-data"></a>Migrer des données

L’étape finale consiste à migrer vos données.

1. Dans l'**Explorateur de métadonnées Oracle**, avec le bouton droit sur **HR**, puis sélectionnez **Migrer des données**.

1. L’étape de migration de données nécessite que vous entrez à nouveau vos informations d’identification Oracle et SQL Server.

1. Lorsque vous avez terminé, passez en revue le rapport de migration de données, qui doit ressembler à la capture d’écran suivante :

   ![Rapport de migration des données](./media/sql-server-linux-convert-from-oracle/DataMigrationReport.png)

## <a name="next-steps"></a>Étapes suivantes

Pour un schéma Orcale plus complexe, le processus de conversion implique davantage de temps, de test et les modifications éventuellement apportées aux applications clientes. L’objectif de ce didacticiel consiste à montrer comment vous pouvez utiliser SSMA pour Oracle dans le cadre de votre processus de migration globale.

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> * Installer SSMA sur Windows
> * Créez un projet SSMA
> * Évaluer et exécuter une migration à partir d’Oracle

Ensuite, explorez les autres façons d’utiliser SSMA :

> [!div class="nextstepaction"]
>[Documentation de l’Assistant Migration SQL Server](../sql-server-migration-assistant.md)
