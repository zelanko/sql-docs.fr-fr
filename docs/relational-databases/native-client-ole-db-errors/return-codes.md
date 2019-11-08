---
title: Codes de retour | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- SQL Server Native Client OLE DB provider, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
ms.assetid: 7f7457e9-fce4-400c-82e5-ee02e9e811c6
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 36f376710dbcdd09daf664e9eee20533c5372641
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73790237"
---
# <a name="return-codes"></a>Codes de retour
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Au niveau le plus élémentaire, une fonction membre réussit ou échoue. À un niveau plus précis, une fonction peut réussir, mais son succès peut ne pas être ce que le développeur d'applications prévoyait.  
  
 Pour plus d’informations sur les codes de retour OLE DB, consultez [Codes de retour (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Quand une fonction membre du fournisseur OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne S_OK, la fonction a réussi.  
  
 Quand une fonction membre du fournisseur OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne retourne pas S_OK, le DÉCOMPRESSION HRESULT OLE/COM a échoué et les macros de IS_ERROR peuvent déterminer le succès ou l’échec global d’une fonction.  
  
 En cas d’échec ou si IS_ERROR retourne la valeur TRUE, le consommateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur est assuré que l’exécution de la fonction membre a échoué. En cas d’échec ou de IS_ERROR retournent la valeur FALSe et HRESULT n’est pas égal à S_OK, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client natif OLE DB fournisseur est assuré que la fonction a réussi d’une certaine manière. Le consommateur peut récupérer des informations détaillées sur ce retour de « réussite avec informations » à partir des interfaces d’erreur du fournisseur OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En outre, dans le cas où une fonction échoue clairement (la macro ayant échoué retourne la valeur TRUE), les informations d’erreur étendues sont disponibles à partir des interfaces d’erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients Native Client OLE DB fournisseur rencontrent généralement le retour HRESULT DB_S_ERRORSOCCURRED « réussite avec les informations ». En général, les fonctions membres qui retournent DB_S_ERRORSOCCURRED définissent un ou plusieurs paramètres qui remettent les valeurs d'état au consommateur. Comme aucune information d'erreur ne peut être disponible au consommateur autre que celle retournée dans les paramètres état-valeur, les consommateurs doivent implémenter la logique d'application pour extraire les valeurs d'état lorsqu'elles sont disponibles.  
  
 Les fonctions membres du fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB ne retournent pas le code de réussite S_FALSE. Toutes les fonctions membres [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur retournent toujours S_OK pour indiquer la réussite de l’opération.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
