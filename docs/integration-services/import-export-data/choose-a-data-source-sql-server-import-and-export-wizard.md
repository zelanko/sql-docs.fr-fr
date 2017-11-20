---
title: "Choisissez une Source de données (SQL Server Assistant Importation et exportation) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
caps.latest.revision: 124
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 80d35cb294fd900611c73ca37bba2a66baef0767
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a>Choisir une source de données (Assistant Importation et Exportation SQL Server)
  Après la page d’accueil, l’Assistant Importation et exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche **Choisir une source de données**. Dans cette page, vous indiquez la source de vos données et la façon de s’y connecter.
  
Pour plus d’informations sur les sources de données que vous pouvez utiliser, consultez [Quelles sont les sources et destinations de données que je peux utiliser ?](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

## <a name="screen-shot-of-the-choose-a-data-source-page"></a>Capture d’écran de la page Choisir une source de données 
La capture d’écran suivante montre la première partie de la page **Choisir une source de données** de l’Assistant. Le reste de la page a un nombre variable d’options qui dépendent de la source de données que vous choisissez ici.

![Choisir la source](../../integration-services/import-export-data/media/choose-source.png)

## <a name="choose-a-data-source"></a>Choisir une source de données
 **Source de données**  
Spécifiez la source de données en sélectionnant le fournisseur de données qui peut se connecter à la source.

-   **Le fournisseur de données dont vous avez besoin est généralement indiquée par son nom**, car le nom du fournisseur contient généralement le nom de la source de données - par exemple, *fichier plat* Source, Microsoft *Excel*, Microsoft *accès*, .net Framework Data Provider for *SqlServer*, .net Framework Data Provider for *Oracle*.

-   **Si vous avez un pilote ODBC pour votre source de données**, sélectionnez .net Framework Data Provider pour ODBC. Puis entrez les informations spécifiques au pilote. Pilotes ODBC ne sont pas répertoriées dans la liste déroulante des sources de données. Le .net Framework Data Provider pour ODBC agit comme un wrapper autour du pilote ODBC. Pour plus d’informations, consultez [se connecter à une Source de données ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **Plusieurs fournisseurs peuvent être disponibles pour votre source de données.** En général, vous pouvez sélectionner n’importe quel fournisseur qui fonctionne avec votre source. Par exemple, pour se connecter à Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez utiliser le fournisseur de données .NET Framework pour SQL Server ou le pilote ODBC de SQL Server. (D’autres fournisseurs sont toujours dans la liste, mais ne sont plus prises en charge.) 

## <a name="my-data-source-isnt-in-the-list"></a>Source de données n’est pas dans la liste
-   **Vous devrez peut-être télécharger le fournisseur de données** à partir de Microsoft ou d’un tiers. La liste des fournisseurs de données disponibles dans le **source de données** liste inclut uniquement les fournisseurs installés sur votre ordinateur. Pour plus d’informations sur les sources de données que vous pouvez utiliser, consultez [Quelles sont les sources et destinations de données que je peux utiliser ?](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

-   **Vous avez un pilote ODBC pour votre source de données ?** Pilotes ODBC ne sont pas répertoriées dans la liste déroulante des sources de données. Si vous avez un pilote ODBC pour votre source de données, sélectionnez .net Framework Data Provider pour ODBC. Puis entrez les informations spécifiques au pilote. Le .net Framework Data Provider pour ODBC agit comme un wrapper autour du pilote ODBC. Pour plus d’informations, consultez [se connecter à une Source de données ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **fournisseurs 32 bits et 64 bits.** Si vous exécutez l’Assistant 64 bits, vous ne voyez pas des sources de données qu’un fournisseur 32 bits est installé et vice versa.

> [!NOTE]
> Pour utiliser la version 64 bits du SQL Server Assistant Importation et exportation, vous devez installer SQL Server. SQL Server Data Tools (SSDT) et SQL Server Management Studio (SSMS) sont des applications 32 bits et installent uniquement les fichiers de 32 bits, y compris la version 32 bits de l’Assistant.

## <a name="after-you-choose-a-data-source"></a>Une fois que vous avez choisi une source de données
Une fois que vous choisissez une source de données, le reste de la **choisir une Source de données** page comporte un nombre variable d’options qui varient selon le fournisseur de données que vous choisissez.

Pour vous connecter à une source de données couramment utilisées, consultez une des pages suivantes.
-   [Se connecter à SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Connexion à Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter à des fichiers plats (fichiers texte)](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter à Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter à Access](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter avec ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter au stockage d’objets Blob Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [Se connecter à PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter à MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

Pour plus d’informations sur la façon de se connecter à une source de données qui n’est pas répertoriée ici, consultez [la référence de chaînes de connexion](https://www.connectionstrings.com/). Ce site tiers contient des exemples de chaînes de connexion et plus d’informations sur les fournisseurs de données et les informations de connexion que dont ils ont besoin.

## <a name="whats-next"></a>Étape suivante  
 Une fois que vous avez fourni les informations relatives à la source de vos données et indiqué comment s’y connecter, la page **Choisir une destination**s’affiche. Dans cette page, vous fournissez les informations relatives à la destination de vos données et à la façon de s’y connecter. Pour plus d’informations, consultez [Choisir une destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).
 
## <a name="see-also"></a>Voir aussi
[Bien démarrer avec cet exemple simple de l’Assistant Importation et Exportation](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



