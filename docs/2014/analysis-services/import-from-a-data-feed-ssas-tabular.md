---
title: Importer à partir d’un flux de données (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0686e519-67c2-4f9b-8cd2-84a4871499ee
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bcb3a1cbcabc66492bbd780be4716ce69f15de37
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66080569"
---
# <a name="import-from-a-data-feed-ssas-tabular"></a>Importer à partir d'un flux de données (SSAS Tabulaire)
  Les flux de données désignent un ou plusieurs flux de données XML générés à partir d'une source de données en ligne et transmis en continu à un document ou une application de destination. Vous pouvez importer des données à partir d'un flux de données dans votre modèle à l'aide de l'Assistant Importation de table.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Fonctionnement de l'importation à partir d'un flux de données](#prereq)  
  
-   [Importer des données à partir d'un dataset Azure DataMarket](#azure)  
  
-   [Importer des flux de données à partir de sources de données publiques ou d'entreprise](#importdata)  
  
-   [Importer des flux de données à partir de listes SharePoint](#importlist)  
  
-   [Importer des flux de données à partir de rapports Reporting Services](#importreport)  
  
##  <a name="prereq"></a> Fonctionnement de l'importation à partir d'un flux de données  
 Vous pouvez importer des données dans un modèle tabulaire à partir des types suivants de flux de données :  
  
 **Rapport Reporting Services**  
 Vous pouvez utiliser un rapport Reporting Services qui a été publié sur un site SharePoint ou sur un serveur de rapports comme source de données dans un modèle. Lors de l'importation de données à partir d'un rapport Reporting Services, vous devez spécifier un fichier de définition de rapport (.rdl) en tant que source de données.  
  
 **Dataset Azure DataMarket**  
 Azure DataMarket est un service qui fournit un canal de remise et de marché unique pour obtenir des informations en tant que services en nuage. Les datasets Azure DataMarket requièrent une clé de compte au lieu d'un compte d'utilisateur Windows.  
  
 **Flux Atom**  
 Le flux doit être un flux Atom. Les flux RSS ne sont pas pris en charge. Le flux doit être disponible publiquement ou vous devez être autorisé à vous y connecter avec le compte Windows avec lequel vous êtes actuellement connecté.  
  
 Les données d'un flux de données sont ajoutées dans un modèle une fois au cours de l'importation. Pour obtenir des données à jour à partir du flux, vous pouvez soit actualiser les données du générateur de modèles, soit configurer une planification d'actualisation des données pour le modèle après qu'il a été déployé sur une instance de production d'Analysis Services. Pour plus d’informations, consultez [Traiter les données &#40;SSAS Tabulaire&#41;](process-data-ssas-tabular.md).  
  
##  <a name="azure"></a> Importer des données à partir d'un dataset Azure DataMarket  
 Vous pouvez importer des données à partir d'un dataset Azure DataMarket comme table dans votre modèle.  
  
#### <a name="to-import-data-from-an-azure-datamarket-dataset"></a>Pour importer des données à partir d'un dataset Azure DataMarket  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Importer à partir de la source de données**. L'Assistant Importation de table s'ouvre.  
  
2.  Dans la page **Connexion à une source de données** , sous **Flux de données**, sélectionnez **Dataset Azure DataMarket**, puis cliquez sur **Suivant**.  
  
3.  Dans la page **Connexion à un dataset Azure DataMarket** , dans **Nom convivial**, tapez un nom descriptif pour le flux auquel vous accédez. Si vous importez plusieurs flux ou sources de données, l'utilisation de noms descriptifs pour la connexion vous aide à vous souvenir de la façon dont la connexion est utilisée.  
  
4.  Dans **URL du flux de données**, tapez l’adresse du flux de données.  
  
5.  Dans **Paramètres de sécurité**, dans **Clé de compte**, tapez une clé de compte. Les clés de compte sont utilisées par Analysis Services pour accéder aux abonnements DataMarket.  
  
6.  Cliquez sur **Tester la connexion** pour vérifier que le flux est disponible. Vous pouvez également cliquer sur **Avancé** pour vérifier que le champ URL de base ou URL du document de service contient la requête ou le document de service qui fournit le flux.  
  
7.  Cliquez sur **Suivant** pour continuer l’importation.  
  
8.  Dans la page **Informations d’emprunt d’identité** , spécifiez les informations d’identification qu’Analysis Services utilisera pour se connecter à la source de données lors de l’actualisation des données, puis cliquez sur **Suivant**. Ces informations d'identification sont différentes de la clé de compte.  
  
9. Dans la page **Sélectionner des tables et des vues** de l’Assistant, dans le champ **Nom convivial** , tapez un nom descriptif identifiant la table qui contiendra ces données après l’importation.  
  
10. Cliquez sur **Afficher un aperçu et filtrer** pour examiner les données et modifier les sélections de colonnes. Vous ne pouvez pas restreindre les lignes qui sont importées dans le flux de données de rapport, mais vous pouvez supprimer des colonnes en désactivant les cases à cocher correspondantes. Cliquez sur **OK**.  
  
11. Dans la page **Sélectionner des tables et des vues** , cliquez sur **Terminer**.  
  
##  <a name="importdata"></a> Importer des flux de données à partir de sources de données publiques ou d'entreprise  
 Vous pouvez accéder à des flux publics ou concevoir des services de données personnalisés qui génèrent des flux Atom à partir de systèmes de base de données privés ou d'ancienne génération.  
  
#### <a name="to-import-data-from-public-or-corporate-data-feeds"></a>Pour importer des données à partir de flux de données publiques ou d'entreprise  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Importer à partir de la source de données**. L'Assistant Importation de table s'ouvre.  
  
2.  Dans la page **Connexion à une source de données** , sous **Flux de données**, sélectionnez **Autres flux**, puis cliquez sur **Suivant**.  
  
3.  Dans la page **Connexion à un flux de données** , tapez un nom descriptif pour le flux auquel vous accédez. Si vous importez plusieurs flux ou sources de données, l'utilisation de noms descriptifs pour la connexion vous aide à vous souvenir de la façon dont la connexion est utilisée.  
  
4.  Dans **URL du flux de données**, tapez l’adresse du flux de données. Les valeurs valides sont les suivantes :  
  
    1.  Document XML qui contient les données Atom. Par exemple, l'URL suivante pointe vers un flux public dans le site Web OGDI (Open Government Data Initiative) :  
  
        ```  
        http://ogdi.cloudapp.net/v1/dc/banklocations/  
        ```  
  
    2.  Document .atomsvc qui spécifie un ou plusieurs flux. Un document .atomsvc pointe vers un service ou une application qui fournit un ou plusieurs flux. Chaque flux est spécifié sous la forme d'une requête de base qui retourne l'ensemble de résultats.  
  
         Vous pouvez spécifier l'adresse URL d'un document .atomsvc situé sur un serveur Web ou ouvrir le fichier à partir d'un dossier partagé ou local sur votre ordinateur. Vous pouvez posséder un document .atomsvc si vous l'avez enregistré sur votre ordinateur pendant l'exportation d'un rapport Reporting Services, ou vous pouvez disposer de documents .atomsvc dans une bibliothèque de flux de données qu'un utilisateur a créée pour votre site SharePoint.  
  
        > [!NOTE]  
        >  La spécification d'un document .atomsvc accessible par le biais d'une adresse URL ou d'un dossier partagé est recommandée car cette opération vous offre la possibilité de configurer par la suite l'actualisation automatique des données pour le classeur, une fois ce dernier publié sur SharePoint. Le serveur peut réutiliser la même adresse URL ou le même dossier réseau pour actualiser les données si vous spécifiez un emplacement non local sur votre ordinateur.  
  
5.  Cliquez sur **Tester la connexion** pour vérifier que le flux est disponible. Vous pouvez également cliquer sur **Avancé** pour vérifier que le champ URL de base ou URL du document de service contient la requête ou le document de service qui fournit le flux.  
  
6.  Cliquez sur **Suivant** pour continuer l’importation.  
  
7.  Dans la page **Informations d’emprunt d’identité** , spécifiez les informations d’identification qu’Analysis Services utilisera pour se connecter à la source de données lors de l’actualisation des données, puis cliquez sur **Suivant**.  
  
8.  Dans la page **Sélectionner des tables et des vues** de l’Assistant, dans le champ **Nom convivial** , remplacez le contenu du flux de données par un nom descriptif identifiant la table qui contiendra ces données après l’importation  
  
9. Cliquez sur **Afficher un aperçu et filtrer** pour examiner les données et modifier les sélections de colonnes. Vous ne pouvez pas restreindre les lignes qui sont importées dans le flux de données de rapport, mais vous pouvez supprimer des colonnes en désactivant les cases à cocher correspondantes. Cliquez sur **OK**.  
  
10. Dans la page **Sélectionner des tables et des vues** , cliquez sur **Terminer**.  
  
##  <a name="importlist"></a> Importer des flux de données à partir de listes SharePoint  
 Vous pouvez importer n’importe quelle liste SharePoint comportant un bouton **Exporter en tant que flux de données** sur le ruban (SharePoint). Vous pouvez cliquer sur ce bouton pour exporter la liste en tant que flux.  
  
#### <a name="to-import-data-feeds-from-a-sharepoint-list"></a>Pour importer des flux de données à partir d'une liste SharePoint  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Importer à partir de la source de données**.  
  
2.  Dans la page **Connexion à une source de données** , sous **Flux de données**, sélectionnez **À partir d’autres flux de données**puis cliquez sur **Suivant**.  
  
3.  Dans la page **Connexion à un flux de données** , tapez un nom descriptif pour le flux auquel vous accédez. Si vous importez plusieurs flux ou sources de données, l'utilisation de noms descriptifs pour la connexion peut vous aider à vous souvenir de la façon dont la connexion est utilisée.  
  
4.  Dans l’URL du flux de données, tapez l’adresse au service de données de liste, en remplaçant \<server-name > par le nom réel de votre serveur SharePoint :  
  
    ```  
    http://<server-name>/_vti_bin/listdata.svc  
    ```  
  
5.  Cliquez sur **Tester la connexion** pour vérifier que le flux est disponible. Vous pouvez également cliquer sur **Avancé** pour vérifier que le champ URL du document de service contient l’adresse du service de données de liste.  
  
6.  Cliquez sur **Suivant** pour continuer l’importation.  
  
7.  Dans la page **Informations d’emprunt d’identité** , spécifiez les informations d’identification qu’Analysis Services utilisera pour se connecter à la source de données lors de l’actualisation des données, puis cliquez sur **Suivant**.  
  
8.  Dans la page **Sélectionner des tables et des vues** de l’Assistant, sélectionnez les listes à importer.  
  
    > [!NOTE]  
    >  Vous pouvez uniquement importer des listes qui contiennent des colonnes.  
  
9. Cliquez sur **Afficher un aperçu et filtrer** pour examiner les données et modifier les sélections de colonnes. Vous ne pouvez pas restreindre les lignes qui sont importées dans le flux de données de rapport, mais vous pouvez supprimer des colonnes en désactivant les cases à cocher correspondantes. Cliquez sur **OK**.  
  
10. Dans la page **Sélectionner des tables et des vues** , cliquez sur **Terminer**.  
  
##  <a name="importreport"></a> Importer des flux de données à partir de rapports Reporting Services  
 Si vous avez un déploiement de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Reporting Services, vous pouvez utiliser l’extension de rendu Atom pour générer un flux de données à partir d’un rapport existant.  
  
#### <a name="to-import-report-data-from-a-published-reporting-services-report"></a>Pour importer des données de rapport à partir d'un rapport Reporting Services publié  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Importer à partir de la source de données**.  
  
2.  Dans la page **Connexion à une source de données** , sous **Flux de données**, sélectionnez **Rapport**, puis cliquez sur **Suivant**.  
  
3.  Sur la page Connexion à un rapport Microsoft SQL Server Reporting Services, dans Nom convivial de la connexion, tapez un nom descriptif pour le flux auquel vous accédez. Si vous importez plusieurs sources de données, l'utilisation de noms descriptifs pour la connexion peut vous aider à vous souvenir de la façon dont la connexion est utilisée.  
  
4.  Cliquez sur **Parcourir** , puis sélectionnez un serveur de rapports.  
  
     Si vous utilisez régulièrement des rapports sur un serveur de rapports, le serveur peut figurer dans **Sites et serveurs récents**. Sinon, dans le champ Nom, tapez l’adresse d’un serveur de rapports, puis cliquez sur **Ouvrir** pour parcourir les dossiers sur le site du serveur de rapports. Un exemple d’adresse pour un serveur de rapports peut être http://\<nom_ordinateur > / reportserver.  
  
5.  Sélectionnez le rapport et cliquez sur **Ouvrir**. Vous pouvez également coller un lien vers le rapport, notamment le chemin complet et le nom du rapport, dans la zone de texte **Nom** . L'Assistant Importation de table se connecte au rapport et le restitue dans la zone d'aperçu.  
  
     Si le rapport utilise des paramètres, vous devez spécifier un paramètre ou vous ne pourrez pas établir de connexion avec le rapport. Lorsque vous procédez ainsi, seules les lignes associées à la valeur du paramètre sont importées dans le flux de données.  
  
    1.  Choisissez un paramètre à l'aide de la zone de liste ou de la zone de liste déroulante fournie dans le rapport.  
  
    2.  Cliquez sur **Afficher le rapport** pour mettre à jour les données.  
  
        > [!NOTE]  
        >  La consultation du rapport enregistre les paramètres que vous avez sélectionnés avec la définition du flux de données.  
  
     Éventuellement, cliquez sur **Avancé** pour définir des propriétés spécifiques au fournisseur pour le rapport.  
  
6.  Cliquez sur **Tester la connexion** pour vérifier que le rapport est disponible en tant que flux de données. Vous pouvez également cliquer sur **Avancé** pour vérifier que la propriété **Document de service en ligne** contient un document XML incorporé qui spécifie la connexion au flux de données.  
  
7.  Cliquez sur **Suivant** pour continuer l’importation.  
  
8.  Dans la page **Informations d’emprunt d’identité** , spécifiez les informations d’identification qu’Analysis Services utilisera pour se connecter à la source de données lors de l’actualisation des données, puis cliquez sur **Suivant**.  
  
9. Dans la page **Sélectionner des tables et des vues** de l’Assistant, cochez la case en regard des parties du rapport que vous voulez importer en tant que données.  
  
     Certains rapports peuvent contenir plusieurs parties, notamment des tables, des listes et des graphiques.  
  
10. Dans la zone **Nom convivial** , tapez le nom de la table dans laquelle vous souhaitez que le flux de données soit enregistré dans votre modèle.  
  
     Le nom du contrôle Reporting Services est utilisé par défaut si aucun nom n'a été affecté : par exemple, Tablix1, Tablix2. Nous vous recommandons de modifier ce nom durant l'importation afin que vous puissiez identifier plus facilement la source et la nature du flux de données importé.  
  
11. Cliquez sur **Afficher un aperçu et filtrer** pour examiner les données et modifier les sélections de colonnes. Vous ne pouvez pas restreindre les lignes qui sont importées dans le flux de données de rapport, mais vous pouvez supprimer des colonnes en désactivant les cases à cocher correspondantes. Cliquez sur **OK**.  
  
12. Dans la page **Sélectionner des tables et des vues** , cliquez sur **Terminer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données prises en charge &#40;SSAS tabulaire&#41;](tabular-models/data-sources-supported-ssas-tabular.md)   
 [Types de données pris en charge &#40;SSAS Tabulaire&#41;](tabular-models/data-types-supported-ssas-tabular.md)   
 [Emprunt d’identité &#40;SSAS Tabulaire&#41;](tabular-models/impersonation-ssas-tabular.md)   
 [Traiter les données &#40;SSAS Tabulaire&#41;](process-data-ssas-tabular.md)   
 [Importer des données &#40;SSAS Tabulaire&#41;](import-data-ssas-tabular.md)  
  
  
