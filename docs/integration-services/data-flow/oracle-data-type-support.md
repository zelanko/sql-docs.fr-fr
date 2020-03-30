---
title: Prise en charge des types de données par le Connecteur Microsoft pour Oracle | Microsoft Docs
ms.custom: ''
ms.date: 08/14/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c28efd8106056ea900fef0cd57791837cf79e21a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "69553229"
---
# <a name="microsoft-connector-for-oracle-data-type-support"></a>Prise en charge des types de données par le Connecteur Microsoft pour Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Les composants SSIS pour Oracle ne prennent pas en charge tous les types de données Oracle. Les colonnes avec des types de données non pris en charge présenteront un avertissement lors de la conception des packages dans SSDT et seront supprimées des colonnes de mappage. Les données ne peuvent pas être chargées dans une colonne dont le type de données n’est pas pris en charge.

## <a name="data-type-mapping"></a>Mappage de types de données

Le tableau suivant présente les types de données de base de données Oracle et leur mappage par défaut aux types de données SSIS. Il montre également les types de données Oracle non pris en charge.

|Type de données de base de données Oracle|Type de données SSIS|Commentaires|
|:-|:-|:-|
|VARCHAR2|DT_STR||
|NVARCHAR2|DT_WSTR||
|CHAR|DT_STR||
|NUMBER|DT_R8|Peut être remplacé par DT_NUMERIC avec une précision et une échelle spécifiques. La précision et l’échelle sont définies par l’utilisateur en fonction des besoins. La sortie sera constituée des données de la colonne sous la forme d’un nombre avec une précision et une échelle fixes.|
|NUMBER(P, S)| Quand l’échelle est égale à 0, en fonction de la précision (P) <li> DT_I1 <Li> DT_I2 <Li> DT_I4 <Li> DT_NUMBERIC(P,0)||
||DT_NUMERIC(P,S)||
|DATE|DT_DBTIMESTAMP||
|<li>timestamp <li>TIMESTAMP WITH TIME ZONE <li>INTERVAL YEAR TO MONTH <li>INTERVAL DAY TO SECOND <li>TIMESTAMP WITH LOCAL TIME ZONE|DT_STR||
|RAW|DT_BYTES||
|CLOB|DT_TEXT|Les types de données CLOB, NCLOB et BLOB sont pris en charge uniquement en mode tableau, et non en mode de chargement rapide.|
|NCLOB|DT_NTEXT||
|BLOB|DT_IMAGE||
|UROWID|Non pris en charge||
|REF|Non pris en charge||
|BFILE|Non pris en charge||
|LONG|Non pris en charge||
|LONG RAW|Non pris en charge||
|ROWID|Non pris en charge||
|Type défini par l’utilisateur (type d’objet, VARRAY, table imbriquée)|Non pris en charge||

## <a name="next-steps"></a>Étapes suivantes

- Configurer le [Gestionnaire de connexions Oracle](oracle-connection-manager.md).
- Configurer la [Source Oracle](oracle-source.md).
- Configurer la [Destination Oracle](oracle-destination.md).
- Si vous avez des questions, rendez-vous sur [TechCommunity](https://aka.ms/AA5u35j).
