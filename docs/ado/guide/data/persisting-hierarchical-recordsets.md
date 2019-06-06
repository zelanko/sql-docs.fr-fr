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
manager: jroth
ms.openlocfilehash: f25b61ca54b3a4ac15584ecf31874f90787c735d
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700468"
---
# <a name="persisting-hierarchical-recordsets"></a>Persistance des recordsets hiérarchiques
Vous pouvez enregistrer une liste hiérarchique **Recordset** dans un fichier au format ADTG ou XML en appelant le [enregistrer](../../../ado/reference/ado-api/save-method.md) (méthode). Toutefois, deux limitations s’appliquent lors de l’enregistrement hiérarchique **Recordset**s au format XML : Vous ne pouvez pas enregistrer au format XML si l’hiérarchique **Recordset** contient en attente de mises à jour, et vous ne pouvez pas enregistrer un paramétrable hiérarchique **Recordset**.  
  
 Pour plus d’informations sur le fournisseur de mise en forme des données, consultez [Microsoft Data Shaping Service pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (ADO) et [vue d’ensemble du Service de mise en forme des données pour OLE DB](https://msdn.microsoft.com/9f51e471-8e85-448e-9fb8-b64bbf767bf3).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)   
 [Grammaire de la mise en forme formelle](../../../ado/guide/data/formal-shape-grammar.md)   
 [Généralités sur les commandes SHAPE](../../../ado/guide/data/shape-commands-in-general.md)
