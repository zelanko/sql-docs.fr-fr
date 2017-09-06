---
title: "Implémentation d’une classe DataReader pour une Extension de traitement de données | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: cfd3a6cb38c59b1810d046839cb3be4f0dc9846a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a>Implémentation d'une classe DataReader pour une extension pour le traitement des données
  Le **DataReader** objet permet à un client récupérer un flux de données en lecture seule et avant uniquement à partir d’une source de données. Les résultats que la requête s’exécute et sont stockés dans la mémoire tampon de réseau sur le client jusqu'à ce que vous les demandez à l’aide de la **en lecture** méthode de la **DataReader** classe. Pour créer un **DataReader** classe, implémentez <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> et, éventuellement, <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>. À l’aide un **DataReader** objet augmente performances de l’application en extrayant les données dès qu’il sont disponible, et non en attente pour tous les résultats de la requête doit être retournée et (par défaut) le stockage qu’une seule ligne à la fois dans la mémoire, ce qui réduit la surcharge du système.  
  
 Après avoir créé une instance de votre **commande** (classe), vous créez un **DataReader** objet en appelant **Command.ExecuteReader** pour extraire des lignes à partir de la source de données. Le **DataReader** implémentation doit fournir deux fonctions de base : accès avant uniquement sur le résultat définit obtenu en exécutant une commande et l’accès aux types de colonne, noms et valeurs dans chaque ligne. Les clients utilisent le **en lecture** méthode de la **DataReader** objet pour obtenir une ligne à partir des résultats de la requête.  
  
 Dans le Concepteur de rapports, votre **DataReader** objet est utilisé pour récupérer la liste des champs, ainsi que des informations de schéma sur le jeu de résultats. Cela est accompli en implémentant la **GetName**, **GetValue**, **GetFieldType,** et **GetOrdinal** méthodes de la <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> interface.  
  
 L'interface <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> vous permet de fournir des informations d'agrégation spécifiques à propos de votre jeu de résultats. Pour obtenir un exemple **DataReader** implémentation de la classe, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implémentation d’une Extension de traitement des données](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
