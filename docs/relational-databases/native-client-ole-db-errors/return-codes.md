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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 09056c9d4964ad10b2b25f63ef5991a1a7742cab
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301018"
---
# <a name="return-codes"></a>Codes de retour
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Au niveau le plus élémentaire, une fonction membre réussit ou échoue. À un niveau plus précis, une fonction peut réussir, mais son succès peut ne pas être ce que le développeur d'applications prévoyait.  
  
 Pour plus d’informations sur les codes de retour OLE DB, consultez [Codes de retour (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Lorsqu’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonction de membre du fournisseur de DB OLE De client autochtone revient S_OK, la fonction a réussi.  
  
 Lorsqu’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonction de membre du fournisseur de DB OLE de client autochtone ne retourne pas S_OK, le FAILED ET IS_ERROR macros d’OLE/COM HRESULT peuvent déterminer le succès ou l’échec global d’une fonction.  
  
 Si FAILED ou IS_ERROR retourne VRAI, le consommateur fournisseur de fournisseur de DB OLE de client autochtone est assuré que l’exécution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la fonction de membre a échoué. Lorsque FAILED ou IS_ERROR retourner FALSE et le HRESULT n’est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pas égal S_OK, le consommateur fournisseur de fournisseur de DB OLE de client autochtone est assuré que la fonction a réussi dans un certain sens. Le consommateur peut récupérer des informations détaillées sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ce retour « succès avec information » des interfaces d’erreur du fournisseur de DB OLE de client autochtone. En outre, dans le cas où une fonction échoue clairement (la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] macro FAILED renvoie VRAI), des informations d’erreur étendues sont disponibles à partir des interfaces d’erreur du fournisseur native OLE DB.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Les consommateurs fournisseurs de fournisseurs de services OLE DB de clients autochtones sont généralement confrontés au rendement DB_S_ERRORSOCCURRED « succès avec l’information » HRESULT. En général, les fonctions membres qui retournent DB_S_ERRORSOCCURRED définissent un ou plusieurs paramètres qui remettent les valeurs d'état au consommateur. Comme aucune information d'erreur ne peut être disponible au consommateur autre que celle retournée dans les paramètres état-valeur, les consommateurs doivent implémenter la logique d'application pour extraire les valeurs d'état lorsqu'elles sont disponibles.  
  
 Les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctions de membre du fournisseur de fournisseurs natives OLE DB ne retournent pas le code de réussite S_FALSE. Toutes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les fonctions de fournisseur de fournisseurs de DB OLE de client autochtone reviennent toujours S_OK pour indiquer le succès.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
