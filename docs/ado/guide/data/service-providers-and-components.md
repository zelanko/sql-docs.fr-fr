---
title: Fournisseurs de services et composants | Microsoft Docs
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
ms.openlocfilehash: a78db07f5ba445c54108558b2ff222bd217c2bbe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924244"
---
# <a name="service-providers-and-components"></a>Fournisseurs et composants de services
Les fournisseurs de services sont des composants qui étendent les fonctionnalités des fournisseurs de données en implémentant des interfaces étendues qui ne sont pas prises en charge en mode natif par le magasin de données.  
  
 Universal Data Access fournit une *architecture de composant* qui permet à des composants individuels spécialisés d’implémenter des jeux discrets de fonctionnalités de base de données, ou « services », sur des magasins moins performants. Par conséquent, au lieu de forcer chaque magasin de données à fournir sa propre implémentation de fonctionnalités étendues ou d’obliger les applications génériques à implémenter les fonctionnalités de base de données en interne, les composants de service offrent une implémentation commune que n’importe quelle application peut Utilisez lors de l’accès à n’importe quel magasin de données. Le fait que certaines fonctionnalités soient implémentées en mode natif par le magasin de données et d’autres par le biais de composants génériques est transparent pour l’application.  
  
 Par exemple, un moteur de curseur, tel que [le service de curseur pour OLE DB](https://msdn.microsoft.com/57638feb-4ecd-4051-becb-8f828d21cf44), est un composant de service qui peut consommer des données d’un magasin de données séquentielles en avant uniquement pour produire des données défilantes. Les autres fournisseurs de services couramment utilisés par ADO incluent le [fournisseur de persistance microsoft OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (pour l’enregistrement de données dans un fichier), le [service de mise en forme de données microsoft pour les OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (pour les **jeux d’enregistrements**hiérarchiques) et le [fournisseur de services Microsoft OLE DB Remoting](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)  
  
 Pour plus d’informations sur le service et les fournisseurs de données, consultez [annexe A : fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md).
