---
title: Microsoft Connectors for Oracle et Teradata par Attunity (SSIS) | Documents Microsoft
ms.date: 05/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 926c0c51b5a55a2869b73666f5620fa56e139cca
ms.openlocfilehash: fd8b0177227167f6caa3417029bb2acb974fe181
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="microsoft-connectors-for-oracle-and-teradata-by-attunity-for-integration-services-ssis"></a>Microsoft Connectors for Oracle et Teradata par Attunity pour Integration Services (SSIS)

Vous pouvez télécharger des connecteurs pour les Services d’intégration par Attunity optimiser les performances lors du chargement des données vers ou à partir d’Oracle ou Teradata dans un package SSIS.

## <a name="download-the-latest-attunity-connectors"></a>Télécharger les dernière connecteurs Attunity

Obtenir la dernière version des connecteurs ici :  
[V5.0 Microsoft Connectors for Oracle and Teradata](https://www.microsoft.com/download/details.aspx?id=55179)

## <a name="issue---the-attunity-connectors-arent-visible-in-the-ssis-toolbox"></a>Problème - les connecteurs Attunity ne sont pas visibles dans la boîte à outils SSIS

Pour afficher les connecteurs Attunity dans la boîte à outils SSIS, vous devez toujours installer la version des connecteurs que cibles de la même version de SQL Server en tant que la version de SQL Server Data Tools (SSDT) installées sur votre ordinateur. (Vous devez également les versions antérieures de connecteurs installés.) Cette exigence est indépendante de la version de SQL Server que vous souhaitez cibler dans vos projets SSIS et vos packages.

Par exemple, si vous avez installé la version la plus récente de SSDT, vous disposez version 17 de SSDT avec un numéro de build qui commence par 14. Cette version de SSDT ajoute la prise en charge de SQL Server 2017. Voir et utiliser le Attunity connecteurs dans SSIS package development - même si vous souhaitez cibler une version antérieure de SQL Server, vous devez également installer la dernière version des connecteurs Attunity, version 5.0. Cette version des connecteurs ajoute également la prise en charge de SQL Server 2017.

Vérifiez la version installée de SSDT dans Visual Studio à partir de **aide** | **sur Microsoft Visual Studio**, ou dans **programmes et fonctionnalités** dans le panneau de configuration. Ensuite, installez la version correspondante des connecteurs Attunity dans le tableau suivant.

|Version SSDT|Numéro de version SSDT|Version de SQL Server cible|Version requise de connecteurs|
|---------|---------|---------|---------|
|17|Commence par 14|SQL Server 2017|[V5.0 Microsoft Connectors for Oracle and Teradata](https://www.microsoft.com/download/details.aspx?id=55179)|
|16|Commence par 13|SQL Server 2016|[Version 4.0 de Microsoft Connectors for Oracle and Teradata](https://www.microsoft.com/download/details.aspx?id=52950)|
||||

## <a name="download-the-latest-sql-server-data-tools-ssdt"></a>Télécharger le dernier SQL Server Data Tools (SSDT)

Obtenir la version la plus récente de SSDT ici :  
[Télécharger SSDT (SQL Server Data Tools)](..//ssdt/download-sql-server-data-tools-ssdt.md)
