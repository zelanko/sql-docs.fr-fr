---
title: Les composants et les fournisseurs de services | Microsoft Docs
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
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9bebbf4c89a04474cbf2d0c88704603cb4c3fef3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700391"
---
# <a name="service-providers-and-components"></a>Fournisseurs et composants de services
Fournisseurs de services sont des composants qui étendent les fonctionnalités des fournisseurs de données en implémentant les interfaces étendues qui ne sont pas prise en charge par le magasin de données.  
  
 Accès aux données universel fournit un *architecture du composant* qui permet à des composants individuels spécialisés à implémenter des ensembles indépendants de fonctionnalités de base de données, ou « services », sur des magasins moins performant. Par conséquent, plutôt que de magasins de données pour fournir sa propre implémentation de fonctionnalité étendue ou de forcer les applications génériques pour implémenter les fonctionnalités de base de données en interne, les composants de service fournissent une implémentation commune n’importe quelle application peut utiliser pour accéder à n’importe quel magasin de données. Le fait que certaines fonctionnalités sont implémentée en mode natif par le magasin de données et certains à travers les composants génériques est transparent pour l’application.  
  
 Par exemple, un curseur de moteur, tel que [le Service de curseur pour OLE DB](https://msdn.microsoft.com/57638feb-4ecd-4051-becb-8f828d21cf44), est un composant de service qui peut utiliser des données à partir d’un magasin de données séquentielles et en avant uniquement pour produire des données à défilement. Incluent d’autres fournisseurs de services couramment utilisés par ADO le [Microsoft OLE DB Persistence Provider (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (pour l’enregistrement des données dans un fichier,) la [Microsoft Data Shaping Service pour OLE DB (fournisseur de services ADO) ](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (pour hiérarchique **Recordsets**) et le [fournisseur Microsoft OLE DB communication à distance (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md) (pour l’appel des fournisseurs de données sur un ordinateur distant).  
  
 Pour plus d’informations sur les fournisseurs de données et de service, consultez [annexe a : Fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md).
