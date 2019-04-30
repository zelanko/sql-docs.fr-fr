---
title: Codes de retour | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 625d56a38d88b3cccbea1c75ad88917af1a6f6dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63228940"
---
# <a name="return-codes"></a>Codes de retour
  Au niveau le plus élémentaire, une fonction membre réussit ou échoue. À un niveau plus précis, une fonction peut réussir, mais son succès peut ne pas être ce que le développeur d'applications prévoyait.  
  
 Pour plus d’informations sur les codes de retour OLE DB, consultez [Codes de retour (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Quand un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonction membre du fournisseur OLE DB Native Client retourne S_OK, la fonction a réussi.  
  
 Quand un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonction membre du fournisseur OLE DB Native Client ne retourne pas S_OK, les macros OLE/COM HRESULT décompactage de FAILED et IS_ERROR peuvent déterminer la réussite ou l’échec d’une fonction globale.  
  
 Si FAILED ou IS_ERROR retourne la valeur TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client est assuré que l’exécution de la fonction membre a échoué. Lorsque FAILED ou IS_ERROR retourne FALSE et que HRESULT n’est pas égal S_OK, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client est assuré que la fonction a réussi d’une certaine façon. Le consommateur peut récupérer des informations détaillées sur ce « réussi avec informations » retourne à partir de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interfaces d’erreur fournisseur OLE DB Native Client. En outre, dans le cas où une fonction échoue clairement (la macro FAILED retourne TRUE), les informations d’erreur étendues sont disponibles à partir de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interfaces d’erreur fournisseur OLE DB Native Client.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consommateurs du fournisseur OLE DB du Client natifs rencontrent généralement le retour HRESULT de DB_S_ERRORSOCCURRED « réussi avec informations ». En général, les fonctions membres qui retournent DB_S_ERRORSOCCURRED définissent un ou plusieurs paramètres qui remettent les valeurs d'état au consommateur. Comme aucune information d'erreur ne peut être disponible au consommateur autre que celle retournée dans les paramètres état-valeur, les consommateurs doivent implémenter la logique d'application pour extraire les valeurs d'état lorsqu'elles sont disponibles.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctions membre du fournisseur OLE DB Native Client ne retournent pas le code de réussite S_FALSE. Tous les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctions membre du fournisseur OLE DB Native Client retournent toujours S_OK pour indiquer la réussite.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](errors.md)  
  
  
