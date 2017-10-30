---
title: Choisir une Destination (SQL Server Assistant Importation et exportation) | Documents Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
caps.latest.revision: 104
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 4ff3c7c8413bd6b535e1c5f95e2a7b06b397c053
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a>Choisir une destination (Assistant Importation et Exportation SQL Server)
 Une fois que vous avez fourni les informations relatives à la source de vos données et indiqué comment s’y connecter, l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche **Choisir une destination**. Dans cette page, vous fournissez les informations relatives à la destination de vos données et à la façon de s’y connecter.
  
Pour plus d’informations sur les destinations de données que vous pouvez utiliser, consultez [Quelles sources de données et destinations puis-je utiliser ?](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources). 

## <a name="screen-shot-of-the-destination-page"></a>Capture d’écran de la page Destination
La capture d’écran suivante montre la première partie de la page **Choisir une destination** de l’Assistant. Le reste de la page a un nombre variable d’options qui dépendent de la destination que vous choisissez ici.

![Choisir une destination](../../integration-services/import-export-data/media/choose-destination.png)

## <a name="choose-a-destination"></a>Choisir une destination
 **Destination**  
 Spécifiez la destination en sélectionnant le fournisseur de données qui peut importer les données dans la destination.
 
-   **Le fournisseur de données dont vous avez besoin est généralement indiquée par son nom**, car le nom du fournisseur contient généralement le nom de la destination - par exemple, *fichier plat* Destination, Microsoft *Excel*, Microsoft *accès*, .net Framework Data Provider for *SqlServer*, .net Framework Data Provider for *Oracle*.

-   **Si vous avez un pilote ODBC pour votre destination**, sélectionnez .net Framework Data Provider pour ODBC. Puis entrez les informations spécifiques au pilote. Pilotes ODBC ne sont pas répertoriées dans la liste déroulante des destinations. Le .net Framework Data Provider pour ODBC agit comme un wrapper autour du pilote ODBC. Pour plus d’informations, consultez [se connecter à une Source de données ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **Plusieurs fournisseurs peuvent être disponibles pour votre destination.** En général, vous pouvez sélectionner n’importe quel fournisseur qui fonctionne avec votre destination. Par exemple, pour se connecter à Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez utiliser le fournisseur de données .NET Framework pour SQL Server ou le pilote ODBC de SQL Server. (D’autres fournisseurs sont toujours dans la liste, mais ne sont plus prises en charge.) 

## <a name="my-destination-isnt-in-the-list"></a>Mon destination n’est pas dans la liste
-   **Vous devrez peut-être télécharger le fournisseur de données** à partir de Microsoft ou d’un tiers. La liste des fournisseurs de données disponibles dans le **Destination** liste inclut uniquement les fournisseurs installés sur votre ordinateur. Pour plus d’informations sur les destinations que vous pouvez utiliser, consultez [les destinations et les sources de données puis-je utiliser ?](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

-   **Vous avez un pilote ODBC pour votre destination ?** Pilotes ODBC ne sont pas répertoriées dans la liste déroulante des destinations. Si vous avez un pilote ODBC pour la destination, sélectionnez .net Framework Data Provider pour ODBC. Puis entrez les informations spécifiques au pilote. Le .net Framework Data Provider pour ODBC agit comme un wrapper autour du pilote ODBC. Pour plus d’informations, consultez [se connecter à une Source de données ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **fournisseurs 32 bits et 64 bits.** Si vous exécutez l’Assistant 64 bits, vous ne voyez pas destinations qu’un fournisseur 32 bits est installé et vice versa.

> [!NOTE]
> Pour utiliser la version 64 bits du SQL Server Assistant Importation et exportation, vous devez installer SQL Server. SQL Server Data Tools (SSDT) et SQL Server Management Studio (SSMS) sont des applications 32 bits et installent uniquement les fichiers de 32 bits, y compris la version 32 bits de l’Assistant.

## <a name="after-you-choose-a-destination"></a>Après avoir choisi une destination
Après avoir choisi une destination, le reste de la **choisir une Destination** page comporte un nombre variable d’options qui varient selon le fournisseur de données que vous choisissez.

Pour vous connecter à une destination couramment utilisée, consultez une des pages suivantes.
-   [Se connecter à SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Connexion à Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter à des fichiers plats (fichiers texte)](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter à Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter à Access](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter avec ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter au stockage d’objets Blob Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [Se connecter à PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [Se connecter à MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

Pour plus d’informations sur la façon de se connecter à une destination qui n’est pas répertoriée ici, consultez [la référence de chaînes de connexion](https://www.connectionstrings.com/). Ce site tiers contient des exemples de chaînes de connexion et plus d’informations sur les fournisseurs de données et les informations de connexion que dont ils ont besoin.

## <a name="whats-next"></a>Étape suivante  
 Une fois que vous avez fourni les informations relatives à la destination de vos données et à la façon de s’y connecter, la page suivante est **Spécifier la copie ou l’interrogation de table**. Dans cette page, vous indiquez si vous voulez copier la totalité d’une table ou uniquement certaines lignes. Pour plus d’informations, consultez [Spécifier la copie ou l’interrogation de table](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>Voir aussi
[Bien démarrer avec cet exemple simple de l’Assistant Importation et Exportation](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



