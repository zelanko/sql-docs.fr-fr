---
title: Utiliser des flux de données (PowerPivot pour SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 50140fdf-6fd1-41a1-9c14-8ecfb97ba2e1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6efccad47f0d6670c87aeb1e9cc9ef9ec654a138
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66070904"
---
# <a name="use-data-feeds-powerpivot-for-sharepoint"></a>Utiliser des flux de données (PowerPivot pour SharePoint)
  Les flux de données comportent un ou plusieurs flux de données générés à partir d'une source de données en ligne et transmis en continu à un document ou une application de destination. Si vous utilisez PowerPivot pour Excel, les flux peuvent vous aider à obtenir des données d'entreprise ou données métier à partir de sources de données arbitraires et qui s'affichent dans la fenêtre PowerPivot dans votre classeur Excel 2010. Après avoir importé un flux dans un classeur, vous pouvez y faire référence ultérieurement dans toute opération d'actualisation des données que vous planifiez sur un serveur SharePoint.  
  
 La façon dont vous utilisez un flux varie selon que vous utilisez les fonctionnalités d'exportation intégrées dans les applications qui prennent en charge les flux Atom ou que vous créez et utilisez des services de données personnalisés. Les applications capables de publier et de lire des données XML Atom fournissent un transfert de données transparent ; la mécanique des flux et services de données est invisible pour l'utilisateur. À ses yeux, un utilisateur ne fait que déplacer des données d'une application vers un autre.  
  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et Microsoft SharePoint 2010 fournissent des flux de données qui peuvent être utilisés dans les classeurs PowerPivot. Vous pouvez utiliser les informations de cette rubrique pour apprendre à accéder à des flux de rapports et listes que vous avez déjà.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Conditions préalables](#prereq)  
  
 [Créer un flux de données à partir d’une liste SharePoint](#sharepointlist)  
  
 [Créer un flux de données à partir d'un rapport Reporting Services](#rsreport)  
  
 [Créer un flux de données à partir d’un document de service de données](#dsdoc)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> Conditions préalables  
 Vous devez disposer de PowerPivot pour Excel pour importer un flux de données dans Excel 2010.  
  
 Vous devez disposer d'un service Web ou d'un service de données qui fournit des données au format Atom 1.0. [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Et SharePoint 2010 peuvent fournir des données dans ce [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] format.  
  
 Avant de pouvoir exporter une liste SharePoint sous forme de flux de données, vous devez installer ADO.NET Data Services sur le serveur SharePoint. Pour plus d’informations, voir [Installation d’ADO.NET Data Services pour prendre en charge les exportations de flux de données des listes SharePoint](../../sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).  
  
##  <a name="create-a-data-feed-from-a-sharepoint-list"></a><a name="sharepointlist"></a> Créer un flux de données à partir d'une liste SharePoint  
 Dans une batterie de serveurs SharePoint 2010, une liste SharePoint présente un bouton Exporter en tant que flux de données dans le ruban Liste. Vous pouvez cliquer sur ce bouton pour exporter la liste en tant que flux. Pour de meilleurs résultats, Excel 2010 avec l'application cliente PowerPivot doit être installé votre station de travail. L'application cliente PowerPivot est lancée en réponse à l'exportation du flux et crée une table PowerPivot qui contient la liste.  
  
1.  Ouvrez la liste sur votre site SharePoint.  
  
2.  Dans Outils de liste, cliquez sur **Liste**.  
  
3.  Dans Se connecter et exporter, cliquez sur **Exporter en tant que flux de données**.  
  
    > [!NOTE]  
    >  Le bouton **Exporter en tant que flux de données** est ajouté à SharePoint par PowerPivot. Si vous n'avez pas installé PowerPivot pour SharePoint ou si vous n'avez pas activé la fonctionnalité PowerPivot, ce bouton n'est pas disponible.  
  
4.  Cliquez sur **Ouvrir** si PowerPivot pour Excel est installé localement, ou cliquez sur **Enregistrer** pour enregistrer le document .atomsvc sur votre disque dur pour les opérations d'importation ultérieures.  
  
5.  Si vous avez choisi **Ouvrir**, utilisez l'Assistant Importation de table pour importer le flux dans une feuille de travail. Le flux de données est ajouté comme nouvelle table dans la fenêtre PowerPivot.  
  
 Une erreur se produira si ADO.NET Data Services 3.5.1 n'est pas installé sur le serveur SharePoint. Pour plus d’informations sur cette erreur et sur sa résolution, voir [Installation d’ADO.NET Data Services pour prendre en charge les exportations de flux de données des listes SharePoint](../../sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).  
  
##  <a name="create-a-data-feed-from-a-reporting-services-report"></a><a name="rsreport"></a>Créer un flux de données à partir d’un rapport de Reporting Services  
 Si vous avez un déploiement de SQL Server 2008 R2 Reporting Services, vous pouvez utiliser la nouvelle extension de rendu Atom pour générer un flux de données à partir d'un rapport existant. Pour de meilleurs résultats, Excel 2010 avec PowerPivot pour Excel doit être installé sur votre station de travail. L'application cliente PowerPivot est lancée en réponse à l'exportation du flux, et ajoute et met automatiquement en relation les tables et colonnes à mesure qu'elles sont transmises.  
  
 Pour obtenir des instructions sur l’exportation d’un flux de données à partir d’un rapport, consultez [Générer des flux de données à partir d’un rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/generate-data-feeds-from-a-report-report-builder-and-ssrs.md) dans le [fichier d’aide du Générateur de rapports](https://go.microsoft.com/fwlink/?LinkId=154494).  
  
> [!NOTE]  
>  Pour configurer une planification périodique d'actualisation des données qui réimporte les données de rapport dans un classeur PowerPivot publié dans une bibliothèque SharePoint, le serveur de rapports doit être configuré pour l'intégration SharePoint. Pour plus d’informations sur l’utilisation conjointe d’PowerPivot pour SharePoint et de Reporting Services, consultez [configuration et administration d’un serveur de rapports &#40;Reporting Services mode SharePoint&#41;](../../reporting-services/configure-administer-report-server-reporting-services-sharepoint-mode.md).  
  
##  <a name="create-a-data-feed-from-a-data-service-document"></a><a name="dsdoc"></a> Créer un flux à partir d'un document de service de données  
 Si vous avez un service de données personnalisé qui génère des flux Atom, vous pouvez configurer un document de service de données en tant que méthode pour rendre les données accessibles aux utilisateurs et aux applications. Un fichier de *document de service de données* (.atomsvc) spécifie une ou plusieurs connexions à des sources en ligne qui publient des données au format câble Atom. Les documents de service de données peuvent être créés dans une *bibliothèque de flux de données*, qui est une bibliothèque à usage spécifique qui fournit un point d’accès commun pour l’exploration de documents de service de données publiés sur un serveur SharePoint. Les travailleurs de l'information sont autorisés à accéder aux documents de service de données dans la bibliothèque de flux peuvent faire référence à l'URL SharePoint du document pour importer les flux dans leurs classeurs et applications.  
  
1.  Ouvrez une bibliothèque de flux créée par votre administrateur de site. Pour plus d’informations, consultez [créer ou personnaliser une bibliothèque de flux de données &#40;PowerPivot pour SharePoint&#41;](create-or-customize-a-data-feed-library-power-pivot-for-sharepoint.md).  
  
2.  Dans Outils de bibliothèque, cliquez sur **Documents**.  
  
3.  Cliquez sur **Nouveau document**.  
  
4.  Fournissez un nom de fichier et une description.  
  
5.  Spécifiez une ou plusieurs URL qui fournissent le flux :  
  
    1.  L'**URL de base** est facultative. Vous devez la spécifier si un document de service de données fournit plusieurs flux. L'URL de base doit spécifier la partie de l'URL qui est commune à tous les flux (par exemple, le nom du serveur et le site). Si vous créez un document de service de données pour un rapport Reporting Services, l'URL de base correspond à l'URL du serveur de rapports et au rapport.  
  
    2.  L'**URL du service Web** est requise. Sans l'URL de base, cette valeur doit inclure le préfixe http:// ou https:// dans l'adresse. Si vous spécifiez une URL de base, l'URL du service Web est la partie qui suit l'URL de base. Par exemple, si l’URL complète est http://adventure-works/inventory/today.aspx, l’URL de base est http://adventure-works/inventory, et l’URL du service Web est/Today.aspx.  
  
         L'URL du service Web peut inclure des paramètres qui filtrent ou sélectionnent un sous-ensemble de données. L'application ou le service qui fournit le flux doit prendre en charge les paramètres que vous spécifiez dans l'URL.  
  
6.  Entrez le **Nom de la table**, une table pour chaque flux. Cette valeur est requise. Le nom de la table est utilisé par une application cliente qui consomme le flux. Dans PowerPivot pour Excel, le nom de la table est utilisé pour nommer les tables dans la fenêtre PowerPivot qui contient les données importées.  
  
## <a name="see-also"></a>Voir aussi  
 [Activer l’intégration des fonctionnalités PowerPivot pour les collections de sites dans l’administration centrale](activate-power-pivot-integration-for-site-collections-in-ca.md)   
 [Partager des flux de données à l’aide d’une bibliothèque de flux de données &#40;PowerPivot pour SharePoint&#41;](share-data-feeds-using-a-data-feed-library-power-pivot-for-sharepoint.md)  
  
  
