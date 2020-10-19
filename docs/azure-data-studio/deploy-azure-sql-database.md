---
title: Déployer Azure SQL Database par le biais d’un notebook
description: Ce tutoriel montre comment créer une base de données Azure SQL.
author: ninarn
ms.author: ninarn
ms.reviewer: alayu, maghan
ms.topic: tutorial
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 10/14/2020
ms.openlocfilehash: 88bb9fd980da21b20f0faf6f699147d26abe65b9
ms.sourcegitcommit: 76ab3b57718341c6057613c9bd38cf82fb17786e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92060889"
---
# <a name="create-an-azure-sql-database-using-azure-data-studio"></a>Créer une base de données Azure SQL à l’aide d’Azure Data Studio

Vous pouvez créer une base de données Azure SQL en utilisant Azure Data Studio par le biais de l’Assistant Déploiement et de notebooks.

## <a name="pre-requisites"></a>Conditions préalables

 - [Azure Data Studio](download-azure-data-studio.md) est installé
 - Un compte et un abonnement Azure actifs. Si vous n’en avez pas, [créez un compte gratuit](https://azure.microsoft.com/free/).

## <a name="use-the-deployment-wizard"></a>Utiliser l’Assistant Déploiement

Effectuez les étapes suivantes pour utiliser l’Assistant Déploiement, qui vous aidera à configurer les paramètres requis dans une interface utilisateur simple.

Tout d’abord, recherchez et sélectionnez Azure SQL Database dans l’Assistant Déploiement.

 1. Dans Azure Data Studio, sélectionnez la viewlet Connexions dans le volet de navigation gauche.
 2. Sélectionnez le bouton **...** en haut du panneau Connexions, puis choisissez **Nouveau déploiement**.
 3. Dans l’Assistant Déploiement, sélectionnez la vignette **Azure SQL Database** et cochez la case d’acceptation des conditions générales.
 4. Dans la liste déroulante Type de ressource, sélectionnez ce que vous souhaitez créer : une base de données, un serveur de base de données ou un pool élastique. Si vous n’avez pas de base de données SQL dans Azure, nous vous recommandons de commencer par créer une base de données.
 5. Sélectionnez **Créer dans le portail Azure**.

Ensuite, entrez tous les paramètres souhaités pour la création de votre base de données, serveur ou pool. Vous trouverez des conseils sur la configuration de ces paramètres dans la [documentation Azure SQL](https://docs.microsoft.com/azure/azure-sql/database/single-database-create-quickstart?tabs=azure-portal).

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez créé votre base de données, serveur ou pool, vous pouvez [vous connecter à votre base de données et l’interroger](quickstart-sql-database.md) dans Azure Data Studio.
