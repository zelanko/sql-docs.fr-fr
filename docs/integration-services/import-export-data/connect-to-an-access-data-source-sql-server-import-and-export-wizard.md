---
title: "Se connecter à une Source de données Access (SQL Server Assistant Importation et exportation) | Documents Microsoft"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b44c159a-c33d-4f3c-bdb8-9832f35317c8
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 71bb3914e31259bc95a1116c2db03708c0442e8c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="connect-to-an-access-data-source-sql-server-import-and-export-wizard"></a>Se connecter à une Source de données Access (SQL Server Assistant Importation et exportation)
Cette rubrique vous montre comment se connecter à un **Microsoft Access** de source de données à partir de la **choisir une Source de données** ou **choisir une Destination** page de l’importation de SQL Server et l’Assistant Exportation.

La capture d’écran suivante montre un exemple de connexion à une base de données Microsoft Access. Dans cet exemple, il est inutile d’entrer un nom d’utilisateur et un mot de passe, car la base de données cible n’utilise pas un fichier d’informations de groupe de travail.

![Se connecter à Access](../../integration-services/import-export-data/media/connect-to-access.jpg)

## <a name="options-to-specify"></a>Options pour spécifier

> [!NOTE]
> Les options de connexion pour ce fournisseur de données sont les mêmes si l’accès est la source ou la destination. Autrement dit, les options sont les mêmes sur les deux le **choisir une Source de données** et **choisir une Destination** pages de l’Assistant.

**Source de données**  
La liste des fournisseurs de données peut contenir plusieurs entrées pour Microsoft Access. Sélectionnez la dernière version installée, ou la version qui correspond à la version d’Access qui a créé le fichier de base de données.

|Source de données|Version d’Office|
|-------|-------|
|Microsoft Access (Microsoft.ACE.OLEDB.16.0)|Office 2016|
|Microsoft Access (Microsoft.ACE.OLEDB.15.0)|Office 2013|
|Microsoft Access (moteur de base de données Microsoft Access)|Office 2010 et Office 2007|
|Microsoft Access (moteur de base de données Microsoft Jet)|Versions d’Office antérieures à Office 2007|

> [!IMPORTANT]
> Vous devrez peut-être télécharger et installer des fichiers supplémentaires pour se connecter à des bases de données Access. Consultez [obtenir les fichiers que vous devez vous connecter pour accéder à](#officeDownloads) sur cette page pour plus d’informations.

 **Nom de fichier**  
Spécifiez le chemin d’accès et le nom du fichier Microsoft Access. Par exemple, **C:\\MyData.mdb** d’un fichier sur l’ordinateur local, ou  **\\ \\Sales\\base de données\\Northwind.mdb** d’un fichier sur un partage réseau. Ou cliquez sur **Parcourir**. 

 >   [!NOTE] 
 > Si vous cliquez sur **Parcourir** pour localiser le fichier d’accès, le **ouvrir** filtres de boîte de dialogue pour les fichiers avec l’ancien. MDB format et extension de fichier par défaut. Toutefois le fournisseur de données peut également ouvrir des fichiers avec la plus récente. Extension de fichier de format et ACCDB.
  
 **Parcourir**  
 Permet de rechercher le fichier de la base de données à l’aide de la boîte de dialogue **Ouvrir**.  
  
 **Nom d'utilisateur**  
Si un fichier d’informations de groupe de travail est associé à la base de données, fournissez un nom d’utilisateur valide.  
  
 **Mot de passe**  
Si un fichier d’informations de groupe de travail est associé à la base de données, fournissez le mot de passe ici.
 
Si la base de données est protégée par un mot de passe unique pour tous les utilisateurs, consultez [le fichier de base de données n’est protégé par mot de passe ?](#database_password).
  
 **Avancé**  
Spécifier des options avancées, telles que le mot de passe de base de données ou un fichier de groupe de travail par défaut, dans le **propriétés des liaisons de données** boîte de dialogue.  

## <a name="i-dont-see-access-in-the-list-of-data-sources"></a>Je ne vois pas l’accès dans la liste des sources de données
Si vous ne voyez pas l’accès dans la liste des sources de données, vous exécutez l’Assistant 64 bits ? Les fournisseurs pour Excel et Access sont généralement 32 bits et ne sont pas visibles dans l’Assistant 64 bits. Exécutez l’Assistant de 32 bits à la place.

> [!NOTE]
> Pour utiliser la version 64 bits du SQL Server Assistant Importation et exportation, vous devez installer SQL Server. SQL Server Data Tools (SSDT) et SQL Server Management Studio (SSMS) sont des applications 32 bits et installent uniquement les fichiers de 32 bits, y compris la version 32 bits de l’Assistant.

## <a name="officeDownloads"></a>Obtenir les fichiers que vous devez vous connecter pour accéder à  
Vous devrez peut-être télécharger les composants de connectivité pour les sources de données Microsoft Office, y compris Access et Excel, si elles ne sont pas déjà installées. Téléchargez la dernière version des composants de connectivité pour les fichiers Access et Excel ici : [redistribuable de 2016 du moteur de base de données de Microsoft Access](https://www.microsoft.com/download/details.aspx?id=54920).
  
La dernière version des composants peut ouvrir des fichiers créés par les versions antérieures d’Access.

Si l’ordinateur dispose d’une version 32 bits d’Office, vous devez installer la version 32 bits des composants et vous devez également vous assurer que vous exécutez le package en mode 32 bits.

Si vous avez un abonnement Office 365, assurez-vous que vous téléchargez le redistribuable de 2016 moteur de base de données Access et non le Runtime de 2016 pour Microsoft Access. Lorsque vous exécutez le programme d’installation, vous voyez un message d’erreur que vous ne pouvez pas installer le téléchargement côte à côte avec les composants Office-clic. Pour ignorer ce message d’erreur, exécutez l’installation en mode silencieux en ouvrant une fenêtre d’invite de commandes et en exécutant le. Fichier .exe que vous avez téléchargé avec le `/quiet` basculer. Par exemple :

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="database_password"></a>Le fichier de base de données n’est protégé par mot de passe ?
Dans certains cas, une base de données Access est protégée par mot de passe, mais n’est pas un fichier d’informations de groupe de travail à l’aide de. Tous les utilisateurs doivent fournir le mot de passe, mais n’ont pas à entrer un nom d’utilisateur. Pour fournir un mot de passe de base de données, procédez comme suit.

1.  Sur le **choisir une Source de données** ou **choisir une Destination** , cliquez sur le **avancé** bouton pour ouvrir la **propriétés des liaisons de données** boîte de dialogue.  
2.  Dans le **propriétés des liaisons de données** boîte de dialogue, sélectionnez le **tous les** onglet.  
3.  Dans la liste des propriétés et des valeurs, sélectionnez **Jet OLEDB : Database Password**.   
    
    ![Spécifiez le mot de passe, écran 1](../../integration-services/import-export-data/media/specify-access-password-screen-1.jpg) 
4.  Cliquez sur **modifier la valeur** pour ouvrir le **modifier la valeur de propriété** boîte de dialogue.  
    
    ![Spécifiez le mot de passe, l’écran 2](../../integration-services/import-export-data/media/specify-access-password-screen-2.jpg)
5.  Dans le **modifier la valeur de propriété** boîte de dialogue, entrez le mot de passe de base de données.
6.  Cliquez sur **OK** dans chaque boîte de dialogue pour revenir à la **choisir une Source de données** ou **choisir une Destination** page de l’Assistant et continuer.

## <a name="keep-your-autonumber-values-when-you-export-from-access"></a>Conserver les valeurs NuméroAuto lorsque vous exportez à partir d’Access
Pour autoriser les valeurs d’identité existantes dans les données source à insérer dans une colonne d’identité dans la table de destination, choisissez le **insertion d’identité activer** option dans le **mappages de colonnes** boîte de dialogue. Par défaut, la colonne d’identité de destination ne vous permettre généralement insérer des valeurs existantes. Pour afficher le **mappages de colonnes** boîte de dialogue, sélectionnez **modifier les mappages** lorsque vous atteignez le **sélectionner des Tables Source et vues** page de l’Assistant. Pour afficher ces pages, consultez [sélectionner des Tables Source et vues](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) et [mappages de colonnes](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).

En général, si vos clés primaires existantes sont dans une colonne d’identité, une colonne NuméroAuto ou son équivalent, vous devez sélectionner cette option pour conserver les valeurs de vos clés primaires existantes. Sinon, la colonne d’identité de destination assigne de nouvelles valeurs.

## <a name="see-also"></a>Voir aussi
[Choisissez une Source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Choisir une Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


