---
title: Persistance des Recordsets hiérarchiques | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO], persisting
- persisting hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 43798bb5-98a6-4ad6-9bf8-78154b3a1827
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2db4e4b4d3d7d137f4f033e35dd643cb0a2d11bb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666627"
---
# <a name="persisting-hierarchical-recordsets"></a>Persistance des recordsets hiérarchiques
Vous pouvez enregistrer une liste hiérarchique **Recordset** dans un fichier au format ADTG ou XML en appelant le [enregistrer](../../../ado/reference/ado-api/save-method.md) (méthode). Toutefois, deux limitations s’appliquent lors de l’enregistrement hiérarchique **Recordset**s au format XML : vous ne pouvez pas enregistrer au format XML si l’hiérarchique **Recordset** contient en attente de mises à jour, et vous ne pouvez pas enregistrer un paramétrable hiérarchique **Recordset**.  
  
 Pour plus d’informations sur le fournisseur de mise en forme des données, consultez [Microsoft Data Shaping Service pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (ADO) et [vue d’ensemble du Service de mise en forme des données pour OLE DB](http://msdn.microsoft.com/9f51e471-8e85-448e-9fb8-b64bbf767bf3).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)   
 [Grammaire de la mise en forme formelle](../../../ado/guide/data/formal-shape-grammar.md)   
 [Généralités sur les commandes SHAPE](../../../ado/guide/data/shape-commands-in-general.md)
