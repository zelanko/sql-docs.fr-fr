---
title: IBCPSession::BCPColumns (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IBCPSession::BCPColumns (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1b5385d32ef349284f261a457391581b6e28da03
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73789706"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Définit le nombre de champs qui doivent être liés aux colonnes dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT BCPColumns(   
      DBCOUNTITEM nColumns);  
```  
  
## <a name="remarks"></a>Notes  
 En interne, il appelle [IBCPSession::BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) afin de définir les valeurs par défaut pour les données du champ. Ces valeurs par défaut sont obtenues à partir des informations de colonne SQL Server que le fournisseur extrait en interne lorsque le nom de la table est spécifié par le biais de [IBCPSession::BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md).  
  
> [!NOTE]  
>  Cette méthode peut être appelée uniquement après que **BCPInit** a été appelé avec un nom de fichier valide.  
  
 Vous devez appeler cette méthode uniquement si vous envisagez d'utiliser un format de fichier utilisateur qui diffère du format par défaut. Pour plus d'informations sur une description du format de fichier utilisateur par défaut, consultez la méthode **BCPInit** .  
  
 Après avoir appelé la méthode **BCPColumns** , vous devez appeler la méthode **BCPColFmt** pour chaque colonne dans le fichier utilisateur afin de définir complètement un format de fichier personnalisé.  
  
## <a name="arguments"></a>Arguments  
 *nColumns*[in]  
 Nombre total de champs dans le fichier utilisateur. Même si vous vous préparez à copier en bloc les données provenant du fichier utilisateur dans une table SQL Server et n'envisagez pas de copier tous les champs dans le fichier utilisateur, vous devez définir l'argument *nColumns* en spécifiant le nombre total de champs de fichier utilisateur. Les champs omis peuvent alors être spécifiés par le biais de **BCPColFmt**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 S_OK  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s’est produite. Pour obtenir des informations détaillées, utilisez l’interface [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, la méthode **BCPInit** n'a pas été appelée avant cette méthode. Cela se produit également lorsque cette méthode est appelée plus d'une fois pour une opération de copie en bloc.  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
## <a name="see-also"></a>Voir aussi  
 [IBCPSession &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Exécution d'opérations de copie en bloc](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
