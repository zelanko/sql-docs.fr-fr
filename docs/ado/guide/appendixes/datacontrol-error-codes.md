---
title: Codes d’erreur DataControl | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], DataControl
- DataControl errors [ADO]
ms.assetid: 293df9d5-e1a2-406d-9107-07bf7cdc6f96
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7cf56b6614587c333f473136f1cafc72128846a2
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52514383"
---
# <a name="datacontrol-object-error-codes"></a>Codes d’erreur de l’objet DataControl
Le tableau suivant répertorie les [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) codes d’erreur de l’objet. La conversion décimale positive des deux octets faible, la conversion décimale négative du code d’erreur complet et les valeurs hexadécimales sont affichés.

|RDS. Codes d’erreur DataControl|Number|Description|
|---------------------------------|------------|-----------------|
|**IDS_AsyncPending**|4107 -2146824175 0x800A1011|Opération impossible pendant que l’opération asynchrone est en attente.|
|**IDS_BadInlineTablegram**|4105 -2146824183 0x800A1009|Mauvais inline tablegram.|
|**IDS_CantConnect**|4099 -2146824189 0x800A1003|Impossible de se connecter au serveur.|
|**IDS_CantCreateObject**|4100-2146824188 0x800A1004|Impossible de créer l’objet métier.|
|**IDS_CantFindDataspace**|4102 -2146824186 0x800A1006|Propriété de l’espace de données n’est pas valide.|
|**IDS_CantInvokeMethod**|4101 -2146824187 0x800A1005|Méthode ne peut pas être appelée sur l’objet métier.|
|**IDS_CrossDomainWarning**|4112 -2146824170 0x800A1016|Cette page accède à des données sur un autre domaine. Vous souhaitez autoriser cela ? Pour éviter ce message dans Internet Explorer, vous pouvez ajouter un site Web sécurisé à votre zone Sites de confiance sur le **sécurité** onglet de la **Options Internet** boîte de dialogue.|
|**IDS_InvalidADCClientVersion**|4106 -2146824176 0x800A1010|Version du Client RDS non valide - le Client est plus récente que le serveur.|
|**IDS_INVALIDARG**|5376 -2147019520 0x80071500|Un ou plusieurs arguments ne sont pas valides.|
|**IDS_InvalidBindings**|4097-2146824191 0x800A1001|Erreur dans la propriété bindings.|
|**IDS_InvalidParam**|4110 -2146824172 0x800A1014|Un ou plusieurs arguments ne sont pas valides.|
|**IDS_NOINTERFACE**|5377-2147019519 0x80071501|Cette interface n’est pris en charge.|
|**IDS_NotReentrant**|4111-2146824171 0x800A1015|Demande ne peut pas être exécutée pendant que le Gestionnaire d’événements traite toujours.|
|**IDS_ObjectNotSafe**|4103-2146824185 0x800A1007|Paramètres de sécurité sur cet ordinateur interdisent la création d’objet métier.|
|**IDS_RecordsetNotOpen**|4109-2146824173 0x800A1013|**Jeu d’enregistrements** n’est pas ouvert.|
|**IDS_ResetInvalidField**|4108 -2146824174 0x800A1012|Colonne spécifiée dans **SortColumn** ou **FilterColumn** n’existe pas.|
|**IDS_RowsetNotUpdateable**|4104 -2146824184 0x800A1008|Ensemble de lignes non modifiable.|
|**IDS_UnexpectedError**|4351-2146823937 0x800A10FF|Erreur inattendue.|
|**IDS_UpdatesFailed**|4098 -2146824190 0x800A1002|Impossible de mettre à jour de la base de données.|
|**IDS_URLMONNotFound**|4119 -2146824169 0x800A1017|DataControl **URL** propriété nécessite le fichier système Urlmon.dll, qui est introuvable.|

## <a name="see-also"></a>Voir aussi
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)
