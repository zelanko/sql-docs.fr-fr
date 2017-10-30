---
title: "Se connecter à une Source de données (SQL Server Assistant Importation et exportation) | Documents Microsoft"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43fbaca0-36d8-4583-9056-af7010209b87
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: b4411fdd2337d93f15b149febf845fb7b0762c40
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="connect-to-an-excel-data-source-sql-server-import-and-export-wizard"></a>Se connecter à une Source de données (SQL Server Assistant Importation et exportation)
Cette rubrique vous montre comment se connecter à un **Microsoft Excel** de source de données à partir de la **choisir une Source de données** ou **choisir une Destination** page de l’importation de SQL Server et l’Assistant Exportation.

La capture d’écran suivante montre un exemple de connexion à un classeur Microsoft Excel.

![Connexion à Excel](../../integration-services/import-export-data/media/excel-connection.png) 

## <a name="options-to-specify"></a>Options pour spécifier

> [!NOTE]
> Les options de connexion pour ce fournisseur de données sont les mêmes si Excel est la source ou la destination. Autrement dit, les options sont les mêmes sur les deux le **choisir une Source de données** et **choisir une Destination** pages de l’Assistant.

**Chemin de fichier Excel**  
 Spécifiez le chemin d’accès et le nom du fichier Excel. Par exemple :
-   Pour un fichier sur l’ordinateur local, **C:\\MyData.xlsx**.
-   Pour un fichier sur un partage réseau,  **\\ \\Sales\\base de données\\Northwind.xlsx**.

Ou cliquez sur **Parcourir**.  
  
 **Parcourir**  
 Permet de rechercher la feuille de calcul à l’aide de la boîte de dialogue **Ouvrir**.  

> [!NOTE]
> L’Assistant ne peut pas ouvrir un fichier Excel protégé par mot de passe.

 **Version Excel**  
Permet de sélectionner la version d’Excel utilisée par le classeur source.

> [!IMPORTANT]
> Vous devrez peut-être télécharger et installer des fichiers supplémentaires pour se connecter à des fichiers Excel. Consultez [obtenir les fichiers que vous souhaitez vous connecter à Excel](#officeDownloads) sur cette page pour plus d’informations.

**La première ligne possède des noms de colonnes**  
Indiquez si la première ligne des données contient des noms de colonnes.
-   Si les données ne contient pas les noms de colonnes, mais que vous activez cette option, l’Assistant traite la première ligne de source de données comme les noms de colonnes.
-   Si les données contiennent des noms de colonnes, mais que vous désactivez cette option, l’Assistant traite la ligne des noms de colonnes en tant que la première ligne de données.

Si vous spécifiez que les données n’ont des noms de colonne, l’Assistant utilise F1, F2 et ainsi de suite, en tant qu’en-têtes de colonne.

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>Je ne vois pas Excel dans la liste des sources de données
Si vous ne voyez pas dans la liste des sources de données Excel, vous exécutez l’Assistant 64 bits ? Les fournisseurs pour Excel et Access sont généralement 32 bits et ne sont pas visibles dans l’Assistant 64 bits. Exécutez l’Assistant de 32 bits à la place.

> [!NOTE]
> Pour utiliser la version 64 bits du SQL Server Assistant Importation et exportation, vous devez installer SQL Server. SQL Server Data Tools (SSDT) et SQL Server Management Studio (SSMS) sont des applications 32 bits et installent uniquement les fichiers de 32 bits, y compris la version 32 bits de l’Assistant.

## <a name="officeDownloads"></a>Obtenir les fichiers que vous souhaitez vous connecter à Excel  
Vous devrez peut-être télécharger les composants de connectivité pour les sources de données Microsoft Office, notamment Excel et Access, s’ils ne sont pas déjà installés. Téléchargez la dernière version des composants de connectivité pour les fichiers Excel et Access ici : [redistribuable de 2016 du moteur de base de données de Microsoft Access](https://www.microsoft.com/download/details.aspx?id=54920).
  
La dernière version des composants permettre ouvrir des fichiers créés par les versions antérieures d’Excel.

Si l’ordinateur dispose d’une version 32 bits d’Office, vous devez installer la version 32 bits des composants et vous devez également vous assurer que vous exécutez le package en mode 32 bits.

Si vous avez un abonnement Office 365, assurez-vous que vous téléchargez le redistribuable de 2016 moteur de base de données Access et non le Runtime de 2016 pour Microsoft Access. Lorsque vous exécutez le programme d’installation, vous voyez un message d’erreur que vous ne pouvez pas installer le téléchargement côte à côte avec les composants Office-clic. Pour ignorer ce message d’erreur, exécutez l’installation en mode silencieux en ouvrant une fenêtre d’invite de commandes et en exécutant le. Fichier .exe que vous avez téléchargé avec le `/quiet` basculer. Par exemple :

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="see-also"></a>Voir aussi
[Choisissez une Source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Choisir une Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


