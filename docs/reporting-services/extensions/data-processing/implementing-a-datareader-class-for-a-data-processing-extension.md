---
title: Implémentation d’une classe DataReader pour une extension pour le traitement des données | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 46345d27b35a1ed4697c4925990f41c4cdd58426
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50029038"
---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a>Implémentation d'une classe DataReader pour une extension pour le traitement des données
  L’objet **DataReader** permet à un client de récupérer un flux de données avant uniquement et en lecture seule à partir d’une source de données. Les résultats sont retournés à mesure que la requête s’exécute et sont stockés sur le client dans la mémoire tampon réseau jusqu’à ce que vous en fassiez la demande à l’aide de la méthode **Read** de la classe **DataReader**. Pour créer une classe **DataReader**, implémentez <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> et, éventuellement, <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>. Le fait d’utiliser un objet **DataReader** améliore les performances de l’application : d’une part, les données sont récupérées dès qu’elles sont disponibles (plutôt que d’attendre le retour des résultats complets de la requête) et, d’autre part, une seule ligne à la fois est stockée en mémoire par défaut, réduisant ainsi la charge système.  
  
 Après avoir créé une instance de votre classe **Command**, vous créez un objet **DataReader** en appelant **Command.ExecuteReader** pour récupérer des lignes de la source de données. L’implémentation de **DataReader** doit fournir deux fonctions de base : l’accès avant uniquement sur les jeux de résultats obtenus en exécutant une commande et l’accès aux types, noms et valeurs de colonne dans chaque ligne. Les clients utilisent la méthode **Read** de l’objet **DataReader** pour obtenir une ligne des résultats de la requête.  
  
 Dans le Concepteur de rapports, votre objet **DataReader** est utilisé pour récupérer une liste de champs ainsi que des informations de schéma sur le jeu de résultats. Pour cela, vous devez implémenter les méthodes **GetName**, **GetValue**, **GetFieldType** et **GetOrdinal** de l’interface <xref:Microsoft.ReportingServices.DataProcessing.IDataReader>.  
  
 L'interface <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> vous permet de fournir des informations d'agrégation spécifiques à propos de votre jeu de résultats. Pour un exemple d’implémentation de la classe **DataReader**, consultez [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (Exemples Reporting Services pour le produit SQL Server).  
  
## <a name="see-also"></a> Voir aussi  
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implémentation d’une extension pour le traitement des données](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
