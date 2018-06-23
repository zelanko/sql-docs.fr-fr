---
title: IBCPSession::BCPColumns (OLE DB) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPColumns (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3f337a918f1281073a70422db307f2698742d5f5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038796"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
  Définit le nombre de champs qui doivent être liés aux colonnes dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT BCPColumns(   
DBCOUNTITEMnColumns);  
```  
  
## <a name="remarks"></a>Notes  
 Elle appelle en interne [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) pour définir les valeurs par défaut pour les données du champ. Ces valeurs par défaut sont obtenues à partir des informations de colonne SQL Server que le fournisseur extrait en interne lorsque le nom de table est spécifié via [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md).  
  
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
 Une erreur spécifique au fournisseur s’est produite ; Pour plus d’informations, utilisez le [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, la méthode **BCPInit** n'a pas été appelée avant cette méthode. Cela se produit également lorsque cette méthode est appelée plus d'une fois pour une opération de copie en bloc.  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
## <a name="see-also"></a>Voir aussi  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Exécution d'opérations de copie en bloc](../native-client/features/performing-bulk-copy-operations.md)  
  
  