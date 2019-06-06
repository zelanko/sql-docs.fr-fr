---
title: Les Interfaces et les objets ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, objects and interfaces
- objects [ADO]
ms.assetid: d0b7e254-c89f-4406-b846-a060ef038c30
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 48b1f3794828af7f60c1d00313506fa9f9c522c8
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696635"
---
# <a name="ado-objects-and-interfaces"></a>Objets et interfaces ADO
Les relations entre ces objets sont représentées dans le [modèle objet ADO](../../../ado/reference/ado-api/ado-object-model.md).  
  
 Chaque objet peut être contenu dans sa collection correspondante. Par exemple, un [erreur](../../../ado/reference/ado-api/error-object.md) objet peut être contenu dans un [erreurs](../../../ado/reference/ado-api/errors-collection-ado.md) collection. Pour plus d’informations, consultez [Collections ADO](../../../ado/reference/ado-api/ado-collections.md) ou une rubrique de regroupement spécifique.  
  
|||  
|-|-|  
|[IADOCommandConstruction](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)|Utilisé pour récupérer la commande OLE DB sous-jacent à partir d’un objet ADOCommand.|  
|[ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)|Construit un ADO **enregistrement** objet à partir d’un OLE DB **ligne** objet dans une application C/C++.|  
|[ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)|Construit un ADO **Recordset** objet à partir d’un OLE DB **ensemble de lignes** objet dans une application C/C++.|  
|[ADOStreamConstruction, interface](../../../ado/reference/ado-api/adostreamconstruction-interface.md)|Construit un ADO **Stream** objet à partir d’un OLE DB **IStream** objet dans une application C/C++.|  
|[Commande](../../../ado/reference/ado-api/command-object-ado.md)|Définit une commande spécifique que vous avez l’intention d’exécuter par rapport à une source de données.<br /><br /> Le **commande** objet n’est pas sécurisé pour le script.|  
|[Connexion](../../../ado/reference/ado-api/connection-object-ado.md)|Représente une connexion ouverte à une source de données.<br /><br /> Le **connexion** objet est sécurisé pour le script.|  
|[IDSOShapeExtensions, interface](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)|Obtient l’objet de Source de données OLE DB sous-jacent pour le fournisseur SHAPE.|  
|[Erreur](../../../ado/reference/ado-api/error-object.md)|Contient des détails sur les erreurs d’accès aux données qui se rapportent à une seule opération impliquant le fournisseur.<br /><br /> Le **erreur** objet n’est pas sécurisé pour le script.|  
|[Field](../../../ado/reference/ado-api/field-object.md)|Représente une colonne de données avec un type de données commun.|  
|[Paramètre](../../../ado/reference/ado-api/parameter-object.md)|Représente un paramètre ou un argument associé à un **commande** objet basé sur une procédure stockée ou une requête paramétrable.<br /><br /> Le **paramètre** objet n’est pas sécurisé pour le script.|  
|[Propriété](../../../ado/reference/ado-api/property-object-ado.md)|Représente une caractéristique dynamique d’un objet ADO qui est définie par le fournisseur.|  
|[Enregistrement](../../../ado/reference/ado-api/record-object-ado.md)|Représente une ligne d’un **Recordset**, ou un répertoire ou un fichier dans un système de fichiers. Le **enregistrement** objet est sécurisé pour le script.|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|Représente le jeu d’enregistrements à partir d’une table de base ou les résultats d’une commande exécutée. À tout moment, le **Recordset** objet fait référence à un seul enregistrement dans le jeu en tant que l’enregistrement en cours.<br /><br /> Le **Recordset** objet est sécurisé pour le script.|  
|[flux de données](../../../ado/reference/ado-api/stream-object-ado.md)|Représente un flux binaire de données.<br /><br /> Le **Stream** objet est sécurisé pour le script.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Collections ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Propriétés dynamiques ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Constantes énumérées ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Annexe B : Erreurs ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Événements ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Méthodes ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Modèle objet ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Propriétés ADO](../../../ado/reference/ado-api/ado-properties.md)
