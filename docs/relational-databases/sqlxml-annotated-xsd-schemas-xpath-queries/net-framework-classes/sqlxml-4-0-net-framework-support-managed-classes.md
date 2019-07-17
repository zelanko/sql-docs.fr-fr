---
title: Classes managées SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- .NET Framework [SQLXML], Managed Classes
- SQL Server .NET Data Provider
- Managed Classes [SQLXML], about managed classes
- providers [SQLXML], SQL Server .NET Data Provider
- data providers [SQLXML], SQL Server .NET Data Provider
- Managed Classes [SQLXML]
- XML [SQLXML]
- SQLXML Managed Classes
- providers [SQLXML], SQLXML Managed Classes
- data providers [SQLXML], SQLXML Managed Classes
- SQLXML, Managed Classes
ms.assetid: 73a5faeb-dabf-4895-acb5-a9651b646065
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 562b75d19715c0cf52cf8eeaf499f142a2b27080
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119606"
---
# <a name="sqlxml-40-net-framework-support---managed-classes"></a>Prise en charge de SQLXML 4.0 pour Microsoft .NET Framework - Classes managées
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 prend en charge des fonctionnalités qui vous permettent d'écrire des applications pour accéder aux données XML d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], intégrer ces données à l'environnement [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, les traiter et renvoyer les mises à jour à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. 
  
  Les classes managées [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML expose les fonctionnalités de SQLXML 4.0 à l'intérieur de [!INCLUDE[msCoName](../../../includes/msconame-md.md)].NET Framework. Avec les classes managées SQLXML, vous pouvez écrire une application C# pour accéder aux données XML à partir d'une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], placer les données dans l'environnement du .NET Framework, traiter les données et retourner les mises à jour à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] comme DiffGram pour qu'elles soient appliquées. Vous devez utiliser un schéma de mappage lors de l'application des mises à jour à une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide des classes managées SQLXML. Pour obtenir un exemple fonctionnel, consultez [l’accès à des fonctionnalités de SQLXML dans l’environnement .NET](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 Pour utiliser les classes managées SQLXML avec SQLXML 4.0, vous devez installer Microsoft Visual Studio.  
  
> [!NOTE]  
>  Le .NET Framework inclut le fournisseur de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET. Ce fournisseur peut être utilisé pour accéder à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à partir de l'environnement .NET ; toutefois, il ne peut gérer que les requêtes SQL traditionnelles (autrement dit, les requêtes de base de données relationnelle à l'exception des requêtes FOR XML). Vous ne pouvez pas exécuter les modèles XML ou les requêtes XPath côté serveur dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  

 Pour plus d’informations sur l’accessibilité et modification des données dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] au sein de la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework et sur l’utilisation de DiffGrams pour mettre à jour des données dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables, consultez [l’accès à des fonctionnalités de SQLXML dans l’environnement .NET](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
> [!NOTE]  
>  Vous pouvez également écrire des applications [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio pour charger en masse des documents XML à l'aide du chargement en masse XML. Pour plus d’informations, consultez [effectuant charge de XML des données en bloc &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md). Vous devez ajouter une référence à la DLL de chargement en masse XML (Xblkld4.dll) dans votre application. Il s'agit d'une DLL COM pour laquelle Visual Studio .NET crée automatiquement la bibliothèque de wrappers.  
  
  Cette section fournit des exemples d’applications qui montrent comment utiliser le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Classes managées SQLXML :  
 [Exécution de requêtes SQL &#40;Classes managées SQLXML&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-sqlxml-managed-classes.md)  
  [Exécution de requêtes SQL à l’aide de la méthode ExecuteXMLReader](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)  
  [Traitement XML du côté Client &#40;Classes managées SQLXML&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/processing-xml-on-the-client-side-sqlxml-managed-classes.md)  
  [Exécution de requêtes XPath &#40;Classes managées SQLXML&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-sqlxml-managed-classes.md)  
  [L’exécution de requêtes XPath avec des espaces de noms &#40;Classes managées SQLXML&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)  
  [Exécution de fichiers modèles à l’aide de la propriété CommandText](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md)  
  [Exécution de fichiers modèles à l’aide de la propriété CommandStream](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandstream-property.md)  
  [Appliquer une Transformation XSL &#40;Classes managées SQLXML&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md)  
  

  
  
