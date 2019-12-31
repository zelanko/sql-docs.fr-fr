---
title: Type de connexion PowerPivot (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a104c3c7-f118-4d02-9a0f-6859f1469d11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e9b8fb98082fb3509acf50e6546673e86962893c
ms.sourcegitcommit: 381595e990f2294dbf324ef31071e2dd2318b8dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74200419"
---
# <a name="powerpivot-connection-type-ssrs"></a>Type de connexion PowerPivot (SSRS)
  Vous pouvez utiliser l'extension pour le traitement des données SQL Server Analysis Services pour récupérer des données d'un classeur PowerPivot qui est publié dans une Galerie SharePoint PowerPivot.  
  
 Utilisez les informations de cette rubrique pour générer une source de données. Pour obtenir des instructions pas à pas, consultez [Ajouter et vérifier une connexion de données ou une source de données &#40;générateur de rapports et des&#41;SSRS ](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 La source de données PowerPivot doit être publiée dans une Galerie PowerPivot sur un site SharePoint.  
  
 Pour prendre en charge les connexions du Générateur de rapports à un classeur PowerPivot, vous devez disposer de SQL Server 2008 R2 ADOMD.NET sur votre station de travail. Cette bibliothèque cliente est installée avec PowerPivot pour Excel, mais si vous utilisez un ordinateur qui n'a pas cette application, vous devez télécharger et installer ADOMD.NET à partir de la page [SQL Server 2008 Feature Pack](https://www.microsoft.com/download/details.aspx?id=16978).  
  
## <a name="data-source-type"></a>Type de source de données  
 Utilisez le type de source de données de rapport **Microsoft SQL Server Analysis Services**.  
  
## <a name="connection-string"></a>Chaîne de connexion  
 La chaîne de connexion est l’URL vers le classeur PowerPivot publié sur SharePoint dans la Galerie PowerPivot ou une autre bibliothèque http://contoso-srv/subsite/PowerPivotLibrary/ContosoSales.xlsx, par exemple,.  
  
## <a name="credentials"></a>Informations d'identification  
 Spécifiez les informations d'identification nécessaires pour accéder au classeur PowerPivot et au site SharePoint ; par exemple, l'authentification Windows (sécurité intégrée). Pour plus d’informations, consultez [connexions de données, sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ou [spécifier des informations d’identification dans générateur de rapports](../specify-credentials-in-report-builder.md).  
  
## <a name="queries"></a>Requêtes  
 Après vous être connecté à la source de données PowerPivot, utilisez la requête graphique MDX pour créer une requête en explorant et en sélectionnant les données à partir des structures de données sous-jacentes. Après avoir créé une requête, exécutez-la pour visualiser des exemples de données dans le volet Résultats.  
  
 Le Concepteur de requêtes analyse la requête pour déterminer les champs du dataset. Vous pouvez aussi modifier manuellement la collection de champs du dataset dans le volet **Données du rapport** . Pour plus d’informations, consultez [Ajouter, modifier ou actualiser des champs dans le volet des données de rapport &#40;Générateur de rapports et SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).  
  
## <a name="filters"></a>Filtres  
 Dans le volet Filtres, spécifiez les dimensions et les membres à exclure par filtrage ou à inclure dans les résultats de la requête.  
  
## <a name="parameters"></a>Paramètres  
 Dans le volet Filtres, sélectionnez l'option **Paramètres** pour qu'un filtre crée automatiquement un paramètre de rapport avec les valeurs disponibles qui correspondent aux sélections de filtre.  
  
## <a name="remarks"></a>Remarques  
 Si vous ouvrez le Générateur de rapports à partir du classeur PowerPivot dans une Galerie PowerPivot, les tableaux croisés dynamiques, graphiques croisés dynamiques, segments et autres mises en page et fonctionnalités analytiques du classeur PowerPivot ne sont pas recréés dans le rapport. À la place, le rapport vide inclut une source de données préconfigurée qui pointe vers les données du classeur PowerPivot. La conception de rapports basés sur un classeur PowerPivot peut être fastidieuse et nécessiter du temps suivant le nombre de segments, de filtres et de tables ou de graphiques que vous voulez recréer dans le rapport. Une meilleure approche consiste à prévoir la présentation des données que vous voulez dans un rapport, indépendamment de la conception PowerPivot.  
  
 Les données contenues dans un classeur PowerPivot sont fortement compressées ; les données récupérées à partir du classeur PowerPivot pour un rapport ne sont pas compressées. Utilisez le concepteur de requêtes pour spécifier des filtres et des paramètres afin de limiter les données à ce qui est absolument nécessaire dans le rapport.  
  
 Contrairement à la connexion à un cube Analysis Services, un modèle PowerPivot n'a pas de hiérarchies. Pour fournir des fonctionnalités semblables aux segments associés dans le classeur, vous devez créer des paramètres en cascade dans le rapport. Pour plus d’informations, consultez [Ajouter des paramètres en cascade à un rapport &#40;Générateur de rapports et SSRS&#41;](../report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md).  
  
 Dans certains cas, vous devrez peut-être ajuster les expressions pour adapter les valeurs de données sous-jacentes du modèle PowerPivot. Vous devrez peut-être modifier des expressions pour convertir les données dans le type de données approprié, ou ajouter ou supprimer une fonction d'agrégation. Par exemple, pour convertir le type de données de Chaîne en Entier, utilisez `=CInt`. Vérifiez toujours que le rapport affiche les valeurs attendues des données dans le modèle PowerPivot avant de publier le rapport.  
  
 Les images d'aperçu d'un rapport dans une Galerie PowerPivot sont générées uniquement si les conditions suivantes sont réunies :  
  
-   Le rapport et le classeur PowerPivot qui fournissent les données doivent être stockés ensemble dans la même Galerie PowerPivot.  
  
-   Le rapport contient uniquement des données PowerPivot provenant d'une source de données PowerPivot.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services interface utilisateur du concepteur de requêtes MDX &#40;Générateur de rapports&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
