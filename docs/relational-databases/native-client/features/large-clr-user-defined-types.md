---
title: Types CLR volumineux définis par l'utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eba57776d99c962460c8c09075b4c2cc39abfd1a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303840"
---
# <a name="large-clr-user-defined-types"></a>Types CLR volumineux définis par l'utilisateur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Dans SQL Server 2005, les types définis par l'utilisateur (UDT) dans le CLR (Common Language Runtime) se limitaient à une taille de 8 000 octets. Cette limite n'est plus d'actualité dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] et versions ultérieures. Les types CLR définis par l'utilisateur sont désormais traités de la même manière que les objets LOB. Ainsi, les types définis par l'utilisateur dont la taille est inférieure ou égale à 8 000 octets adoptent le même comportement que dans SQL Server 2005 mais les types définis par l'utilisateur plus volumineux sont pris en charge et affichent une taille « illimitée ».  
  
 Pour plus d’informations, voir [Grands types définis par l’utilisateur CLR &#40;&#41;OLE DB](../../../relational-databases/native-client/ole-db/large-clr-user-defined-types-ole-db.md) et [les grands types définis par l’utilisateur CLR &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="use-cases"></a>Cas d'utilisation  
 Pour ODBC, la prise en charge des types définis par l'utilisateur volumineux incluent la possibilité de transmettre des valeurs UDT en fragments sous forme de paramètres de données en cours d'exécution. Cela se fait en utilisant SQLPutData.  
  
 Pour OLE DB, la prise en charge des types définis par l’utilisateur volumineux offre la possibilité de diffuser des valeurs UDT vers et depuis le serveur au moyen d’une liaison ISequentialStream.  
  
 Les types définis par l'utilisateur dont la taille est inférieure ou égale à 8 000 octets se comporteront de la même manière que dans SQL Server 2005. Pour OLE DB, vous pouvez toujours transmettre en continu des types définis par l'utilisateur de petite taille à l'aide de la liaison ISequentialStream.  
  
 Le code natif doit quelquefois comprendre le contenu des types CLR définis par l'utilisateur mais n'a pas besoin d'instancier les objets managés. Dans ce cas, vous pouvez utiliser la sérialisation personnalisée pour convertir des valeurs de type défini par l'utilisateur (UDT) sur le serveur dans un format bien connu des clients.  
  
 Pour les applications qui disposent d'un code d'accès aux données existant, vous pouvez exploiter le comportement des types CLR définis par l'utilisateur sur le client en extrayant des types définis par l'utilisateur via des API natives et en les instanciant au moyen de l'interopérabilité C++/CLI dans des applications en mode mixte.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
