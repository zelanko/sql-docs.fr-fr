---
title: "Se connecter à une Source de données ODBC (SQL Server Assistant Importation et exportation) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6318776-a188-48a7-995d-9eafd7148ff2
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 0e3ffe2ff1695de69be7149f4be7b42f57b0e991
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="connect-to-an-odbc-data-source-sql-server-import-and-export-wizard"></a>Se connecter à une Source de données ODBC (SQL Server Assistant Importation et exportation)
Cette rubrique vous montre comment se connecter à un **ODBC** de source de données à partir de la **choisir une Source de données** ou **choisir une Destination** page de l’importation de SQL Server et l’Assistant Exportation.

Vous devrez peut-être télécharger le pilote ODBC nécessaires de Microsoft ou d’un tiers.

Vous devrez peut-être également rechercher les informations de connexion requises que vous devez fournir. Ce site tiers - [la référence de chaînes de connexion](https://www.connectionstrings.com/) -contient des exemples de chaînes de connexion et plus d’informations sur les fournisseurs de données et les informations de connexion dont ils ont besoin.

## <a name="make-sure-the-driver-you-want-is-installed"></a>Assurez-vous que le pilote est installé
1.  Rechercher ou Parcourir pour le **Sources de données ODBC (64 bits)** applet du panneau. Si vous avez uniquement un pilote 32 bits, ou si vous savez que vous devez utiliser un pilote 32 bits, recherchez ou accédez à **Sources de données ODBC (32 bits)** à la place.
2.  Lancez l’application. Le **administrateur de sources de données ODBC** fenêtre s’ouvre.
3.  Sur le **pilotes** onglet, vous trouverez une liste de tous les pilotes ODBC installés sur votre ordinateur. (Les noms de certains des pilotes peuvent figurer dans plusieurs langues.)

    Voici un exemple de la liste des pilotes 64 bits installés.

    ![Pilotes ODBC installés 64 bits](../../integration-services/import-export-data/media/installed-64-bit-odbc-drivers.png)

> [!TIP]
> Si vous savez que de votre pilote installé et que vous ne le voyez dans l’application 64 bits, recherchez dans le panneau de configuration 32 bits à la place. Cela vous indique également si vous devez exécuter le 64 bits ou 32 bits SQL Server Assistant Importation et exportation.
>
> Pour utiliser la version 64 bits du SQL Server Assistant Importation et exportation, vous devez installer SQL Server. SQL Server Data Tools (SSDT) et SQL Server Management Studio (SSMS) sont des applications 32 bits et installent uniquement les fichiers de 32 bits, y compris la version 32 bits de l’Assistant.
    
## <a name="step-1---select-the-data-source"></a>Étape 1 : sélectionnez la source de données
Les pilotes ODBC installés sur votre ordinateur ne sont pas répertoriées dans la liste déroulante des sources de données. Pour vous connecter avec un pilote ODBC, commencez par sélectionner le **fournisseur de données .NET Framework pour ODBC** comme source de données sur le **choisir une Source de données** ou **choisir une Destination** page de l’Assistant. Ce fournisseur agit comme un wrapper autour du pilote ODBC.

Voici l’écran générique que vous voyez immédiatement après avoir sélectionné le fournisseur de données .NET Framework pour ODBC.

![Se connecter à SQL avec ODBC avant](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

## <a name="step-2---provide-the-connection-info"></a>Étape 2 : fournir les informations de connexion
L’étape suivante consiste à fournir les informations de connexion pour votre pilote ODBC et votre source de données. Vous avez le choix entre deux options.
1.  Fournir un **DSN** (nom de source de données) qui existe déjà ou que vous créez avec le **administrateur de sources de données ODBC** applet du panneau. Une source de données est la collection enregistrée des paramètres requis pour se connecter à une source de données ODBC.

    Si vous déjà connaissez le nom de la source de données, ou de savez comment créer une nouvelle source de données maintenant, vous pouvez ignorer le reste de cette page. Entrez le nom de source de données dans le **Dsn** champ sur la **choisir une Source de données** ou **choisir une Destination** page, puis passez à l’étape suivante de l’Assistant.

    [Fournir une source de données](#odbc_dsn)
    
2.  Fournir un **chaîne de connexion**, que vous pouvez rechercher en ligne, ou créer et tester sur votre ordinateur avec le **administrateur de sources de données ODBC** applet.

    Si vous déjà avez la chaîne de connexion ou que vous savez comment créer, vous pouvez ignorer le reste de cette page. Entrez la chaîne de connexion dans le **ConnectionString** champ sur la **choisir une Source de données** ou **choisir une Destination** page, puis passez à l’étape suivante de l’Assistant.

    [Fournissez une chaîne de connexion](#odbc_connstring)

Si vous fournissez une chaîne de connexion, le **choisir une Source de données** ou **choisir une Destination** page affiche toutes les informations de connexion que l’Assistant va utiliser pour se connecter à votre source de données, par exemple, méthode de nom et l’authentification serveur et base de données. Si vous fournissez une source de données, ces informations n’est pas visibles.

## <a name="odbc_dsn"></a>Option 1 - fournir une source de données
Si vous souhaitez fournir les informations de connexion avec un DSN (nom de source de données), utilisez la **administrateur de sources de données ODBC** applet pour rechercher le nom de la source de données existante, ou pour créer une nouvelle source de données.
1.  Rechercher ou Parcourir pour le **Sources de données ODBC (64 bits)** applet du panneau. Si vous seulement les un pilote 32 bits, ou utiliser un pilote 32 bits, recherchez ou accédez à **Sources de données ODBC (32 bits)** à la place.
2.  Lancez l’application. Le **administrateur de sources de données ODBC** fenêtre s’ouvre. Voici à quoi ressemble l’applet.

    ![Panneau de contrôle de l’administrateur ODBC](../../integration-services/import-export-data/media/odbc-administrator-control-panel-applet.png)
    
3.  Si vous souhaitez **utiliser un DSN existant** pour votre source de données, vous pouvez utiliser toute source de données que vous voyez sur le **DSN utilisateur**, **DSN système**, ou **fichier DSN** onglet. Vérifiez le nom, puis revenez à l’Assistant et entrez-la dans la **Dsn** champ sur la **choisir une Source de données** ou **choisir une Destination** page. Ignorez le reste de cette page et continuer à l’étape suivante de l’Assistant.
4.  Si vous souhaitez **créer une nouvelle source de données**, décidez si vous souhaitez qu’il soit visible que par vous (DSN utilisateur), visible pour tous les utilisateurs de l’ordinateur, y compris des services Windows (DSN système) ou enregistrés dans un fichier (fichier DSN). Cet exemple crée une nouvelle source de données système.
5. Sur le **DSN système** , cliquez sur **ajouter**.

    ![Ajouter un nouveau système ODBC DSN](../../integration-services/import-export-data/media/add-a-new-odbc-system-dsn.png)
    
6.  Dans le **créer une nouvelle Source de données** boîte de dialogue, sélectionnez le pilote de votre source de données, puis cliquez sur **Terminer**.

    ![Choisir le pilote pour le nouveau système DSN](../../integration-services/import-export-data/media/pick-driver-for-new-system-dsn.png)
    
7. Le pilote affiche maintenant un ou plusieurs écrans spécifiques au pilote où vous entrez les informations nécessaires pour se connecter à votre source de données. (Pour le pilote SQL Server, par exemple, il existe quatre pages de paramètres personnalisés.) Une fois que vous avez terminé, le nouveau système DSN s’affiche dans la liste.

    ![Nouveau système DSN dans la liste](../../integration-services/import-export-data/media/new-system-dsn-in-list.png)
    
8.  Revenez à l’Assistant et entrez le nom de source de données dans le **Dsn** champ sur la **choisir une Source de données** ou **choisir une Destination** page. Passez à l’étape suivante de l’Assistant.

## <a name="odbc_connstring"></a>Option 2 - fournir une chaîne de connexion
Si vous souhaitez fournir vos informations de connexion avec une chaîne de connexion, le reste de cette rubrique vous aide à obtenir la chaîne de connexion que vous avez besoin.

Cet exemple va utiliser la chaîne de connexion suivante, qui se connecte à Microsoft SQL Server.

    Driver={ODBC Driver 13 for SQL Server};server=localhost;database=WideWorldImporters;trusted_connection=Yes;

Entrez la chaîne de connexion dans le **ConnectionString** champ sur la **choisir une Source de données** ou **choisir une Destination** page. Après avoir entré la chaîne de connexion, l’Assistant analyse la chaîne et affiche les propriétés et leurs valeurs dans la liste.

Voici l’écran que vous voyez après avoir entré la chaîne de connexion.

![Se connecter à SQL avec ODBC après](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-after.jpg)

> [!NOTE]
> Les options de connexion pour un pilote ODBC sont les mêmes si vous configurez votre source ou destination. Autrement dit, les options sont les mêmes sur les deux le **choisir une Source de données** et **choisir une Destination** pages de l’Assistant.

## <a name="get-the-connection-string-online"></a>Obtenir la chaîne de connexion en ligne
Pour rechercher des chaînes de connexion pour votre pilote ODBC en ligne, consultez [la référence de chaînes de connexion](https://www.connectionstrings.com/). Ce site tiers contient des exemples de chaînes de connexion et plus d’informations sur les fournisseurs de données et les informations de connexion que dont ils ont besoin.

## <a name="get-the-connection-string-with-an-app"></a>Obtenir la chaîne de connexion à une application
Pour générer et tester la chaîne de connexion pour votre pilote ODBC sur votre ordinateur, vous pouvez utiliser la **administrateur de sources de données ODBC** applet du panneau. Créer un fichier DSN pour votre connexion, puis copier les paramètres de la source de données de fichier pour assembler la chaîne de connexion. Cela nécessite plusieurs étapes, mais permet de s’assurer que vous avez une chaîne de connexion valide.

1.  Rechercher ou Parcourir pour le **Sources de données ODBC (64 bits)** applet du panneau. Si vous seulement les un pilote 32 bits, ou utiliser un pilote 32 bits, recherchez ou accédez à **Sources de données ODBC (32 bits)** à la place.
2.  Lancez l’application. Le **administrateur de sources de données ODBC** fenêtre s’ouvre.
3.  Passez maintenant à la **fichier DSN** onglet de l’application. Cliquez sur **Ajouter**.

    Pour cet exemple, créez un fichier DSN plutôt que la source de données utilisateur ou DSN système, car le fichier DSN enregistre les paires nom-valeur dans le format spécifique est requis pour la chaîne de connexion.

    ![Ajouter un nouveau fichier ODBC DSN](../../integration-services/import-export-data/media/add-a-new-odbc-file-dsn.png)

4.  Dans le **créer une nouvelle Source de données** boîte de dialogue, sélectionnez votre pilote dans la liste, puis cliquez sur **suivant**. Cet exemple va créer une source de données qui contient les arguments de chaîne de connexion que vous devez vous connecter à Microsoft SQL Server.

    ![Créer la nouvelle source de données ODBC](../../integration-services/import-export-data/media/create-new-odbc-data-source.png)
    
5.  Sélectionnez un emplacement et entrez un nom de fichier pour le nouveau fichier DSN, puis cliquez sur **suivant**. N’oubliez pas où vous enregistrez le fichier afin de pouvoir trouver et ouvrir dans une étape ultérieure.

    ![Enregistrer le nouveau fichier DSN](../../integration-services/import-export-data/media/save-new-file-dsn.png)

6.  Passez en revue le résumé de vos sélections, puis cliquez sur **Terminer**.

7.  Après avoir cliqué sur **Terminer**, le pilote que vous avez sélectionné affiche un ou plusieurs écrans propriétaires pour rassembler les informations qu’il doit se connecter. En général, ces informations incluent server, les informations de connexion et base de données pour les sources de données basées sur le serveur et de fichier, le format et version pour les sources de données de fichiers.

8. Une fois que vous configurez votre source de données, cliquez sur **Terminer**, sont généralement afficher un récapitulatif de vos sélections et avez la possibilité de les tester.

    ![Test nouveau fichier DSN](../../integration-services/import-export-data/media/test-new-file-dsn.png)

9. Une fois que vous testez votre source de données et fermez les boîtes de dialogue, recherchez la source de données du fichier où vous avez enregistré dans le système de fichiers. Si vous n’avez pas de modifier l’extension de fichier, l’extension par défaut est. SOURCE DE DONNÉES.

10. Ouvrez le fichier enregistré avec le bloc-notes ou un autre éditeur de texte. Voici le contenu de notre exemple de SQL Server.

        [ODBC]  
        DRIVER=ODBC Driver 13 for SQL Server  
        TrustServerCertificate=No  
        DATABASE=WideWorldImporters    
        WSID=<local computer name>  
        APP=Microsoft® Windows® Operating System  
        Trusted_Connection=Yes  
        SERVER=localhost   
        
11. Copiez et collez les valeurs nécessaires dans une chaîne de connexion dans lequel les paires nom-valeur sont séparées par des points-virgules.

    Une fois que vous assemblez les valeurs requises à partir de l’exemple de fichier source de données, vous disposez de la chaîne de connexion.
    
        DRIVER=ODBC Driver 13 for SQL Server;SERVER=localhost;DATABASE=WideWorldImporters;Trusted_Connection=Yes

    Vous ne devez généralement tous les paramètres dans une source de données créés par l’administrateur de Source de données ODBC pour créer une chaîne de connexion qui fonctionne.  
    -   Vous devez toujours spécifier le pilote ODBC.
    -   Pour une source de données basée sur un serveur tel que SQL Server, vous devez en général, le serveur, base de données et informations de connexion. Dans l’exemple de source de données, vous n’avez pas besoin TrustServerCertificate, WSID ou application.
    -   Pour une source de données de fichiers, vous devez au moins nom de fichier et emplacement.
    
12. Collez cette chaîne de connexion dans le **ConnectionString** champ sur la **choisir une Source de données** ou **choisir une Destination** page de l’Assistant. L’Assistant analyse la chaîne et vous êtes prêt à continuer.

    ![Se connecter à SQL avec ODBC après](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-after.jpg)

## <a name="see-also"></a>Voir aussi
[Choisissez une Source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Choisir une Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)



