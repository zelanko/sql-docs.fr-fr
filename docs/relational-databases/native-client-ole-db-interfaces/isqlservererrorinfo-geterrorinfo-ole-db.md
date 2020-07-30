---
title: 'ISQLServerErrorInfo :: GetErrorInfo (fournisseur Native Client OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
apitype: COM
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0305e9755f6ccd671d0f3e9fbeb852f2d4393c70
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243910"
---
# <a name="isqlservererrorinfogeterrorinfo-native-client-ole-db-provider"></a>ISQLServerErrorInfo :: GetErrorInfo (fournisseur Native Client OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Retourne un pointeur vers une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] structure SSERRORINFO du fournisseur OLE DB Native Client contenant les détails de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erreur.  
  
 Le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit l'interface d'erreur **ISQLServerErrorInfo** . Cette interface retourne les détails d’une erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], notamment sa gravité et son état.  

  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT GetErrorInfo(  
   SSERRORINFO**ppSSErrorInfo,  
   OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>Arguments  
 *ppSSErrorInfo*[out]  
 Pointeur vers une structure SSERRORINFO. Si la méthode échoue ou qu’il n’existe pas d’informations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associées à l’erreur, le fournisseur n’alloue pas de mémoire et vérifie que l’argument *ppSSErrorInfo* est un pointeur null en sortie.  
  
 *ppErrorStrings*[out]  
 Pointeur vers un pointeur de chaîne de caractère Unicode. Si la méthode échoue ou qu’il n’existe pas d’informations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associées à l’erreur, le fournisseur n’alloue pas de mémoire et vérifie que l’argument *ppErrorStrings* est un pointeur null en sortie. La libération de l’argument *ppErrorStrings* avec la méthode **IMalloc::Free** libère les trois membres de type chaîne individuels de la structure SSERRORINFO retournée, la mémoire étant allouée dans un bloc.  
  
## <a name="return-code-values"></a>Codet de retour  
 S_OK  
 S_OK  
  
 E_INVALIDARG  
 L'argument *ppSSErrorInfo* ou *ppErrorStrings* était NULL.  
  
 E_OUTOFMEMORY  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client n’a pas pu allouer suffisamment de mémoire pour terminer la demande.  
  
## <a name="remarks"></a>Notes  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client alloue de la mémoire pour les chaînes SSERRORINFO et OLECHAR retournées par le biais des pointeurs passés par le consommateur. Le consommateur doit désallouer cette mémoire avec la méthode **IMalloc::Free** quand il n’est plus nécessaire d’accéder aux données d’erreur.  
  
 La structure SSERRORINFO est définie comme suit :  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|Membre|Description|  
|------------|-----------------|  
|*pwszMessage*|Message d'erreur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le message est retourné via la méthode **IErrorInfo::GetDescription**.|  
|*pwszServer*|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur laquelle l'erreur s'est produite.|  
|*pwszProcedure*|Le nom de la procédure stockée qui génère l'erreur si l'erreur s'est produite dans une procédure stockée ; sinon, une chaîne vide.|  
|*lNative*|Numéro d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le numéro d’erreur est identique à celui retourné dans le paramètre *plNativeError* de la méthode **ISQLErrorInfo::GetSQLInfo**.|  
|*bState*|État de l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*bClass*|Gravité de l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Le cas échéant, la ligne d'une procédure stockée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui a généré le message d'erreur. Si aucune procédure n'est impliquée, la valeur par défaut est 1.|  
  
 Pointeurs dans les adresses de type référence de la structure de la chaîne retournée dans l’argument *ppErrorStrings*.  
  
## <a name="see-also"></a>Voir aussi  
 [&#41;&#40;de ISQLServerErrorInfo OLE DB](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
