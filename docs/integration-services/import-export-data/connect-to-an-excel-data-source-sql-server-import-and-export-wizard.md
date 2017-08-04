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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d744e84aa2b4ae0462a5d5a1e4453a9e86abb890
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

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
> Vous devrez peut-être télécharger et installer des fichiers supplémentaires pour vous connecter à la version d’Excel que vous sélectionnez. Consultez [obtenir les fichiers que vous souhaitez vous connecter à Excel](#officeDownloads) sur cette page pour plus d’informations.

Si vous avez un problème lorsque vous spécifiez une version, essayez de spécifier une version différente, même dans une version antérieure. Par exemple, vous ne pouvez pas être en mesure d’installer les fournisseurs de données Office 2016, car vous avez un abonnement Microsoft Office 365. Vous pouvez uniquement installer les fournisseurs de données pour Excel 2016 et accès 2016 avec une version de bureau de Microsoft Office. Dans ce cas, vous pouvez spécifier Excel 2013 au lieu d’Excel 2016. Les deux versions du fournisseur sont fonctionnellement équivalentes. Cette limitation de l’exécution d’Office 2016 est mentionnée dans [ce billet de blog](https://blogs.office.com/2015/12/16/access-2016-runtime-is-now-available-for-download/).

**La première ligne possède des noms de colonnes**  
Indiquez si la première ligne des données contient des noms de colonnes.
-   Si les données ne contient pas les noms de colonnes, mais que vous activez cette option, l’Assistant traite la première ligne de source de données comme les noms de colonnes.
-   Si les données contiennent des noms de colonnes, mais que vous désactivez cette option, l’Assistant traite la ligne des noms de colonnes en tant que la première ligne de données.

Si vous spécifiez que les données n’ont des noms de colonne, l’Assistant utilise F1, F2 et ainsi de suite, en tant qu’en-têtes de colonne.

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>Je ne vois pas Excel dans la liste des sources de données
Si vous ne voyez pas dans la liste des sources de données Excel, vous exécutez l’Assistant 64 bits ? Les fournisseurs pour Excel et Access sont généralement 32 bits et ne sont pas visibles dans l’Assistant 64 bits. Exécutez l’Assistant de 32 bits à la place.

## <a name="officeDownloads"></a>Obtenir les fichiers que vous souhaitez vous connecter à Excel  
Vous devrez peut-être télécharger les composants de connectivité pour les sources de données Microsoft Office, notamment Excel et Access, s’ils ne sont pas déjà installés.

Les versions ultérieures des composants peuvent ouvrir des fichiers créés par les versions antérieures des programmes. Dans certains cas, les versions antérieures des composants peuvent également ouvrir des fichiers créés par les versions ultérieures des programmes. Par exemple, si vous ne pouvez pas installer les composants Office 2016, utilisez à la place les composants Office 2013. Les deux versions du fournisseur sont fonctionnellement équivalentes. Cette limitation de l’exécution d’Office 2016 est mentionnée dans [ce billet de blog](https://blogs.office.com/2015/12/16/access-2016-runtime-is-now-available-for-download/).

Si l’ordinateur dispose d’une version 32 bits d’Office - cela est typique, même sur les ordinateurs 64 bits - vous devez installer la version 32 bits des composants. Vous devez également vous assurer que vous exécutez l’Assistant 32 bits, ou exécutez le package SQL Server Integration Services créés par l’Assistant en mode 32 bits. 
 
|Version de Microsoft Office|Télécharger|  
|------------------------------|--------------|  
|2016|[Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040)|
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/download/details.aspx?id=39358)|
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/download/details.aspx?id=10910)|  
|2007|[Pilote Office System 2007 : composants de connectivité de données](https://www.microsoft.com/download/details.aspx?id=23734)|  

## <a name="see-also"></a>Voir aussi
[Choisissez une Source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Choisir une Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


