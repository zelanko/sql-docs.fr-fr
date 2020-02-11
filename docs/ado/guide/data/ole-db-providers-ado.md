---
title: Fournisseurs de OLE DB (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 6e0488c3-934d-4976-99dc-65c580dc7a3c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7e86375639d875f5cfec21705af47c005afd901e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924757"
---
# <a name="ole-db-providers-ado"></a>Fournisseurs OLE DB (ADO)
OLE DB définit un ensemble d’interfaces COM pour fournir aux applications un accès uniforme aux données stockées dans diverses sources d’informations. Cette approche permet à une source de données de partager ses données via les interfaces qui prennent en charge la quantité de fonctionnalités SGBD appropriées à la source de données. Par défaut, l’architecture hautes performances de OLE DB est basée sur l’utilisation d’un modèle de services flexible basé sur les composants. Au lieu d’avoir un nombre prescrit de couches intermédiaires entre l’application et les données, OLE DB ne nécessite que le nombre de composants nécessaires pour accomplir une tâche particulière.  
  
 Supposons, par exemple, qu’un utilisateur souhaite exécuter une requête. Examinez les scénarios suivants :  
  
-   Les données se trouvent dans une base de données relationnelle pour laquelle il existe actuellement un pilote ODBC mais aucun fournisseur de OLE DB natif : l’application utilise ADO pour communiquer avec le fournisseur OLE DB pour ODBC, qui charge ensuite le pilote ODBC approprié. Le pilote passe l’instruction SQL au SGBD, qui récupère les données.  
  
-   Les données se trouvent dans Microsoft SQL Server pour lesquelles il existe un fournisseur de OLE DB natif : l’application utilise ADO pour communiquer directement avec le fournisseur OLE DB pour Microsoft SQL Server. Aucun intermédiaire n’est requis.  
  
-   Les données résident dans Microsoft Exchange Server, pour lequel il existe un fournisseur de OLE DB, mais qui n’expose pas de moteur pour traiter les requêtes SQL : l’application utilise ADO pour communiquer avec le fournisseur OLE DB pour Microsoft Exchange et appelle sur un processeur de requêtes OLE DB composant pour gérer l’interrogation.  
  
-   Les données résident dans le système de fichiers Microsoft NTFS sous la forme de documents : les données sont accessibles à l’aide d’un fournisseur de OLE DB natif sur le service d’indexation Microsoft, qui indexe le contenu et les propriétés des documents dans le système de fichiers pour permettre un contenu efficace leurs.  
  
 Dans tous les exemples précédents, l’application peut interroger les données. Les besoins de l’utilisateur sont satisfaits avec un nombre minimal de composants. Dans chaque cas, les composants supplémentaires sont utilisés uniquement si nécessaire, et seuls les composants requis sont appelés. Ce chargement à la demande des composants réutilisables et partageables contribue fortement aux performances élevées lorsque OLE DB est utilisé.  
  
 Les fournisseurs se répartissent en deux catégories : celles fournissant des données et celles fournissant des services. Un fournisseur de données possède ses propres données et l’expose sous forme tabulaire à votre application. Un fournisseur de services encapsule un service en générant et en consommant des données, en augmentant les fonctionnalités de vos applications ADO. Un fournisseur de services peut également être défini comme un composant de service, qui doit fonctionner conjointement avec d’autres fournisseurs de services ou composants.  
  
 ADO offre une interface cohérente et de niveau supérieur aux différents fournisseurs de OLE DB.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Fournisseurs de données](../../../ado/guide/data/data-providers.md)  
  
-   [Fournisseurs et composants de services](../../../ado/guide/data/service-providers-and-components.md)
