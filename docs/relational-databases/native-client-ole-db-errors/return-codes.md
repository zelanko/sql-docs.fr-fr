---
title: Codes de retour (fournisseur Native Client OLE DB)
description: En savoir plus sur les codes de retour pris en charge pour SQL Server Native Client OLE DB, y compris la valeur DB_S_ERRORSOCCURRED HRESULT couramment rencontrée.
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 64111973f8e1c753a3d342c395d2f457ad1b3401
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97433727"
---
# <a name="return-codes-native-client-ole-db-provider"></a>Codes de retour (fournisseur Native Client OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Au niveau le plus élémentaire, une fonction membre réussit ou échoue. À un niveau plus précis, une fonction peut réussir, mais son succès peut ne pas être ce que le développeur d'applications prévoyait.  
  
 Pour plus d’informations sur les codes de retour OLE DB, consultez [Codes de retour (OLE DB)](/previous-versions/windows/desktop/ms725451(v=vs.85)).  
  
 Quand une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonction membre du fournisseur OLE DB Native Client retourne S_OK, la fonction a réussi.  
  
 Quand une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonction membre du fournisseur OLE DB Native Client ne retourne pas S_OK, le DÉCOMPRESSION HRESULT OLE/com a échoué et les macros IS_ERROR peuvent déterminer le succès ou l’échec global d’une fonction.  
  
 En cas d’échec ou si IS_ERROR retourne la valeur TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client est assuré que l’exécution de la fonction membre a échoué. En cas d’échec ou de IS_ERROR retournent la valeur FALSe et HRESULT n’est pas égal à S_OK, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client est assuré que la fonction a réussi d’une certaine manière. Le consommateur peut récupérer des informations détaillées sur ce retour de « réussite avec informations » à partir des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interfaces d’erreur du fournisseur OLE DB Native Client. En outre, dans le cas où une fonction échoue clairement (la macro ayant échoué retourne la valeur TRUE), les informations d’erreur étendues sont disponibles à partir des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interfaces d’erreur du fournisseur OLE DB Native Client.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les consommateurs de fournisseurs OLE DB Native Client rencontrent généralement le retour HRESULT DB_S_ERRORSOCCURRED « réussite avec les informations ». En général, les fonctions membres qui retournent DB_S_ERRORSOCCURRED définissent un ou plusieurs paramètres qui remettent les valeurs d'état au consommateur. Comme aucune information d'erreur ne peut être disponible au consommateur autre que celle retournée dans les paramètres état-valeur, les consommateurs doivent implémenter la logique d'application pour extraire les valeurs d'état lorsqu'elles sont disponibles.  
  
 Les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctions membres du fournisseur OLE DB Native Client ne retournent pas le code de réussite S_FALSE. Toutes les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctions membres du fournisseur Native Client OLE DB retournent toujours S_OK pour indiquer la réussite.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
