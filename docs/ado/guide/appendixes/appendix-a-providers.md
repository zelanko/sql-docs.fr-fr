---
title: 'Annexe A : Fournisseurs | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- providers [ADO]
- ADO, providers
- service providers [ADO]
- service components [ADO]
ms.assetid: e2581b47-b11e-4e1e-b96c-d39c77c5b48a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14194998e699fa3d16ab50ab488c8d1577660dcc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62719911"
---
# <a name="appendix-a-data-and-service-providers"></a>Annexe A : Fournisseurs de services et données
Cette section traite des trois types de fournisseurs : fournisseurs de données, les fournisseurs de services et les composants de service. Fournisseurs se répartissent en deux catégories : ceux qui fournissent des données et ceux qui fournissent des services. Un *fournisseur de données* possède ses propres données et les expose sous forme de tableau à votre application. Un *fournisseur de services* encapsule un service en production et la consommation des données, étendant les fonctionnalités de vos applications ADO. Un fournisseur de services peut être également défini comme un *composant de service*, qui doivent travailler avec les autres fournisseurs de services ou des composants.

## <a name="data-providers"></a>Fournisseurs de données
 ADO est puissant et flexible, car il peut se connecter à plusieurs fournisseurs de données et continuer à exposer le même modèle de programmation, indépendamment des fonctionnalités spécifiques de n’importe quel fournisseur donné.

 Cependant, étant donné que chaque fournisseur de données est unique, comment votre application interagit avec ADO varie légèrement par fournisseur de données. Les différences se répartissent généralement en trois catégories :

-   Paramètres de connexion dans le [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) propriété.

-   [Commande](../../../ado/reference/ado-api/command-object-ado.md) l’utilisation de l’objet.

-   Spécifique au fournisseur [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) comportement.

 Détails de chacun des fournisseurs de données actuellement disponibles auprès de Microsoft sont répertoriés comme suit.

|Domaine|Rubrique|
|----------|-----------|
|Bases de données ODBC|[Fournisseur Microsoft OLE DB pour ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)|
|Service d’indexation Microsoft|[Fournisseur Microsoft OLE DB pour le Service d’indexation Microsoft](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md)|
|Service Active Directory|[Fournisseur Microsoft OLE DB pour le Service Microsoft Active Directory](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md)|
|Bases de données Microsoft Jet|[Fournisseur OLE DB pour Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)|
|Microsoft SQL Server|[Fournisseur Microsoft OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)|
|Bases de données Oracle|[Fournisseur Microsoft OLE DB pour Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)|
|Publication Internet|[Fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)|
|Sources de données simple|[Fournisseur Simple Microsoft OLE DB](../../../ado/guide/appendixes/microsoft-ole-db-simple-provider.md)|

## <a name="provider-specific-dynamic-properties"></a>Propriétés dynamiques spécifiques au fournisseur
 Le [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collections de la [connexion](../../../ado/reference/ado-api/connection-object-ado.md), [commande](../../../ado/reference/ado-api/command-object-ado.md), et [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objets incluent des propriétés dynamiques spécifiques à la fournisseur. Ces propriétés fournissent des informations sur les fonctionnalités spécifiques au fournisseur au-delà des propriétés intégrées prenant en charge ADO.

 Après avoir établi la connexion et création de ces objets, utilisez le [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) méthode sur le **propriétés** collection de l’objet à obtenir les propriétés spécifiques au fournisseur. Reportez-vous à la documentation du fournisseur et le [Guide du programmeur OLE DB](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) pour plus d’informations sur ces propriétés dynamiques.

## <a name="service-providers"></a>Fournisseurs de services
 Pour utiliser un fournisseur de services, vous devez fournir un mot clé. Vous devez également connaître les propriétés dynamiques spécifiques au fournisseur associées à chaque fournisseur de services. Les détails spécifiques au fournisseur sont répertoriés pour chaque fournisseur de service est actuellement disponible à partir de Microsoft :

-   [Microsoft Data Shaping Service pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

-   [Fournisseur de persistance Microsoft OLE DB](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)

-   [Fournisseur de communication à distance Microsoft OLE DB](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)

## <a name="service-components"></a>Composants de service
 Le [Service de curseur pour OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) composant de service complète les fonctions de prise en charge de curseur des fournisseurs de données. Il nécessite un mot clé et a des propriétés dynamiques.

 Pour plus d’informations sur les fournisseurs OLE DB, consultez [Microsoft OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx).

## <a name="provider-commands"></a>Commandes de fournisseur
 Pour chaque fournisseur répertorié ici, si vos applications permettent aux utilisateurs d’entrer des instructions SQL en tant que les commandes fournisseur, vous devez toujours valider l’entrée d’utilisateur et être vigilant des attaques possibles à l’aide des instructions SQL potentiellement dangereuses, telles que `DROP TABLE t1`, dans le cadre de l’entrée utilisateur.

## <a name="see-also"></a>Voir aussi
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [objet Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md) [fournisseur Microsoft OLE DB pour le Service Microsoft Active Directory ](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md) [Fournisseur Microsoft OLE DB pour le Service d’indexation Microsoft](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md) [fournisseur Microsoft OLE DB pour ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md) [fournisseur Microsoft OLE DB pour Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) [Fournisseur Microsoft OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) [fournisseur Microsoft OLE DB pour Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) [Collection de propriétés (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [ L’objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [Refresh, méthode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
