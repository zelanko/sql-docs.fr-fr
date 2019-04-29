---
title: Fournisseurs OLE DB (ADO) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: b3f4f1d4efed51a8f9e3b5eaf3bd4a2c7f385e75
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63034990"
---
# <a name="ole-db-providers-ado"></a>Fournisseurs OLE DB (ADO)
OLE DB définit un ensemble d’interfaces COM pour fournir des applications avec un accès uniforme aux données stockées dans diverses sources d’informations. Cette approche permet à une source de données de partager ses données via les interfaces qui prennent en charge de la quantité de fonctionnalités SGBD appropriées pour la source de données. Par conception, l’architecture de haute performance d’OLE DB est basée sur son utilisation d’un modèle de services flexibles, basé sur les composants. Au lieu d’avoir un nombre défini de couches intermédiaires entre l’application et les données, OLE DB ne requiert qu’au moment où de nombreux composants nécessaire pour accomplir une tâche particulière.  
  
 Par exemple, qu'un utilisateur veut exécuter une requête. Examinez les scénarios suivants :  
  
-   Les données résident dans une base de données relationnelle pour laquelle il existe actuellement un pilote ODBC mais aucun fournisseur OLE DB natif : L’application utilise ADO pour communiquer avec le fournisseur OLE DB pour ODBC, lequel charge alors le pilote ODBC approprié. Le pilote transmet l’instruction SQL au SGBD, qui extrait les données.  
  
-   Les données résident dans Microsoft SQL Server pour laquelle il existe un fournisseur OLE DB natif : L’application utilise ADO pour communiquer directement avec le fournisseur OLE DB pour Microsoft SQL Server. Aucun intermédiaires ne sont nécessaires.  
  
-   Les données résident dans Microsoft Exchange Server, pour lequel il existe un fournisseur OLE DB, mais qui n’expose pas un moteur de traitement des requêtes SQL : L’application utilise ADO pour communiquer avec le fournisseur OLE DB pour Microsoft Exchange et appelle un composant processeur de requêtes de OLE DB pour traiter la requête.  
  
-   Les données résident dans le système de fichiers NTFS de Microsoft sous la forme de documents : Données sont accessible à l’aide d’un fournisseur OLE DB natif via le Service d’indexation Microsoft, qui indexe le contenu et les propriétés des documents dans le système de fichiers pour mener des recherches de contenu efficaces.  
  
 Dans les exemples précédents, l’application peut interroger les données. Un nombre minimal de composants correspond aux besoins de l’utilisateur. Dans chaque cas, des composants supplémentaires sont utilisées uniquement si nécessaire, et seuls les composants requis sont appelés. Ce chargement de la demande de composants réutilisables et partageables contribue fortement à hautes performances lorsque OLE DB est utilisé.  
  
 Fournisseurs se répartissent en deux catégories : ceux qui fournissent des données et ceux qui fournissent des services. Un fournisseur de données possède ses propres données et les expose sous forme de tableau à votre application. Un fournisseur de services encapsule un service en produisant et en consommant des données, pour enrichir les fonctionnalités de vos applications ADO. Un fournisseur de services peut être également défini comme un composant de service, qui doit fonctionner conjointement avec d’autres fournisseurs de services ou les composants.  
  
 ADO fournit une cohérence, interface de niveau supérieur pour les différents fournisseurs OLE DB.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Fournisseurs de données](../../../ado/guide/data/data-providers.md)  
  
-   [Fournisseurs et composants de services](../../../ado/guide/data/service-providers-and-components.md)
