---
title: Démarrer l’Assistant Importation et Exportation SQL Server
titleSuffix: Integration Services (SSIS)
ms.prod: sql
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
author: chugugrace
ms.author: chugu
ms.reviewer: ''
ms.custom: ''
ms.date: 11/18/2019
ms.openlocfilehash: e77f176e9c49d095a5f12aa1d653fa7be41ca25e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "74165630"
---
# <a name="start-the-sql-server-import-and-export-wizard"></a>Démarrer l’Assistant Importation et Exportation SQL Server

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Démarrez l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec l’une des méthodes décrites dans cette rubrique pour exporter et importer des données de n’importe quelle source de données prise en charge.

> [!IMPORTANT]
> Cette rubrique explique seulement comment **démarrer** l’Assistant. Si ce n’est pas ce que vous recherchez, consultez [Tâches et contenus connexes](#related-tasks-and-content).

Vous pouvez démarrer l’Assistant :

- À partir du [menu Démarrer](#start-menu).
- À partir du [invite de commandes](#command-prompt).
- À partir de [SQL Server Management Studio (SSMS)](#sql-server-management-studio-ssms).
- À partir de [Visual Studio avec SQL Server Data Tools (SSDT)](#visual-studio).

## <a name="prerequisite---is-the-wizard-installed-on-your-computer"></a>Prérequis - l’Assistant est-il installé sur votre ordinateur ?

Si vous souhaitez exécuter l’Assistant, mais que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas installé sur votre ordinateur, vous pouvez installer l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en installant SSDT (SQL Server Data Tools). Pour plus d’informations, consultez [Télécharger SSDT (SQL Server Data Tools)](https://msdn.microsoft.com/library/mt204009.aspx).

> [!NOTE]
> Pour utiliser la version 64 bits de l’Assistant Importation et Exportation SQL Server, vous devez installer SQL Server. SQL Server Data Tools (SSDT) et SQL Server Management Studio (SSMS) sont des applications 32 bits qui installent uniquement des fichiers 32 bits, y compris la version 32 bits de l’Assistant.

## <a name="start-menu"></a>Menu Démarrer

### <a name="start-the-sql-server-import-and-export-wizard-from-the-start-menu"></a>Démarrage de l’Assistant Importation et Exportation SQL Server à partir du menu Démarrer

1. Dans le menu **Démarrer**, recherchez et développez **Microsoft SQL Server 20xx**.
2. Cliquez sur l’une des options suivantes :
    - **Importer-exporter des données SQL Server 20xx (64 bits)**
    - **Importer-exporter des données SQL Server 20xx (32 bits)**

    Exécutez la version 64 bits de l’Assistant, sauf si vous savez que votre source de données a besoin d’un fournisseur de données 32 bits.

    ![Démarrer l’Assistant (Démarrer)](../../integration-services/import-export-data/media/start-wizard-start-64.png)

## <a name="command-prompt"></a>Invite de commande

### <a name="start-the-sql-server-import-and-export-wizard-from-the-command-prompt"></a>Démarrage de l’Assistant Importation et Exportation SQL Server à partir de l’invite de commandes

Dans une fenêtre d’invite de commandes, exécutez **DTSWizard.exe** à partir d’un des emplacements suivants :

- **C:\Program Files\Microsoft SQL Server\140\DTS\Binn** pour la version 64 bits.
  - *140* = SQL Server 2017.  Cette valeur dépend de la version de SQL Server dont vous disposez.

- **C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn** pour la version 32 bits.
  - *140* = SQL Server 2017.  Cette valeur dépend de la version de SQL Server dont vous disposez.

Exécutez la version 64 bits de l’Assistant, sauf si vous savez que votre source de données a besoin d’un fournisseur de données 32 bits.

![Démarrer l’Assistant (cmd)](../../integration-services/import-export-data/media/start-wizard-cmd.png)
  
## <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)

### <a name="start-the-sql-server-import-and-export-wizard-from-sql-server-management-studio-ssms"></a>Démarrage de l’Assistant Importation et Exportation SQL Server à partir de SQL Server Management Studio (SSMS)

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à une instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].

2. Développez **Bases de données**.

3. Cliquez avec le bouton droit sur le nom d’une base de données.

4. Pointez sur **Tâches**.

5. Cliquez sur l’une des options suivantes :

   - **Importer des données**

   - **Exporter les données**  

   ![Démarrer l’Assistant SSMS](../../integration-services/import-export-data/media/start-wizard-ssms.jpg) 

Si vous n’avez pas installé SQL Server, ou que vous avez installé SQL Server mais pas SQL Server Management Studio, consultez [Télécharger SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).

## <a name="visual-studio"></a>Visual Studio

### <a name="start-the-sql-server-import-and-export-wizard-from-visual-studio-with-sql-server-data-tools-ssdt"></a>Démarrage de l’Assistant Importation et Exportation SQL Server à partir de Visual Studio avec SQL Server Data Tools (SSDT)

 Dans Visual Studio avec [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], après avoir ouvert un projet Integration Services, effectuez l’une des opérations suivantes.

- Dans le menu **Projet** , cliquez sur **Assistant d’importation et d’exportation SSIS**.

   ![Démarrer l’Assistant (projet)](../../integration-services/import-export-data/media/start-wizard-project.png)

   \- ou -

- Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier **Packages SSIS** , puis cliquez sur **Assistant d’importation et d’exportation SSIS**.

    ![Démarrer l’Assistant (packages)](../../integration-services/import-export-data/media/start-wizard-packages.png)

Si vous n’avez pas installé Visual Studio, ou que vous avez installé Visual Studio mais pas SQL Server Data Tools, consultez [Télécharger SSDT (SQL Server Data Tools)](../../ssdt/download-sql-server-data-tools-ssdt.md).

## <a name="get-the-wizard"></a>Se procurer l’Assistant

Si vous souhaitez exécuter l’Assistant, mais que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas installé sur votre ordinateur, vous pouvez installer l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en installant SSDT (SQL Server Data Tools). Pour plus d’informations, consultez [Télécharger SSDT (SQL Server Data Tools)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="get-help-while-the-wizard-is-running"></a>Obtenir de l’aide pendant l’exécution de l’Assistant

> [!TIP]
> Pour afficher la documentation sur une page ou une boîte de dialogue déterminée de l’Assistant, appuyez sur la touche F1 à partir de cette page.   

## <a name="whats-next"></a>Quelle est l’étape suivante ?

Quand vous démarrez l’Assistant, la première page est **Assistant Importation et Exportation SQL Server**. Vous n’avez aucune action à effectuer dans cette page. Pour plus d’informations, consultez [Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md).  
  
## <a name="related-tasks-and-content"></a>Tâches et contenus connexes

Voici d’autres tâches élémentaires.

- **Consulter un exemple rapide sur le fonctionnement de l’Assistant.**

  - **Si vous préférez afficher des captures d’écran.** Regardez cet exemple simple qui tient sur une seule page : [Bien démarrer avec cet exemple simple de l’Assistant Importation et Exportation](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

  - **Si vous préférez regarder une vidéo.** Regardez cette vidéo de quatre minutes sur YouTube qui décrit l’Assistant et explique à l’aide d’instructions claires et simples comment exporter des données vers Excel : [Utilisation de l’Assistant Importation et Exportation SQL Server pour exporter vers Excel](https://go.microsoft.com/fwlink/?linkid=829049).

  - **Approfondir ses connaissances sur le fonctionnement de l’Assistant.**

  - **Découvrez-en plus sur l’Assistant.** Si vous recherchez une vue d’ensemble de l’Assistant, consultez [Importer et exporter des données avec l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

  - **Découvrez-en plus sur les étapes de l’Assistant.** Si vous avez besoin d’informations sur les étapes de l’Assistant, consultez [Étapes de l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). Il existe aussi une page de documentation propre à chaque page de l’Assistant.

  - **Découvrez comment se connecter à des sources et des destinations de données.** Si vous avez besoin d’informations sur la façon de vous connecter à vos données, sélectionnez la page qui vous intéresse à partir de la liste ici : [Se connecter à des sources de données avec l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). Il existe une page de documentation propre à chacune des différentes sources de données couramment utilisées.