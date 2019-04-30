---
title: IBCPSession::BCPColFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColFmt method
ms.assetid: 2852f4ba-f1c6-4c4c-86b2-b77e4abe70de
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e896f3e04d24becf136b7abefcff9dbe97fa0970
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240265"
---
# <a name="ibcpsessionbcpcolfmt-ole-db"></a>IBCPSession::BCPColFmt (OLE DB)
  Crée une liaison entre des variables de programme et des colonnes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT BCPColFmt(   
DBORDINALidxUserDataCol,  
inteUserDataType,  
intcbIndicator,  
intcbUserData,  
BYTE *pbUserDataTerm,  
intcbUserDataTerm,  
DBORDINALidxServerCol);  
```  
  
## <a name="remarks"></a>Notes  
 La méthode **BCPColFmt** permet de créer une liaison entre des champs de fichier de données BCP et des colonnes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il accepte la longueur, le type, la marque de fin et la longueur de préfixe d'une colonne en tant que paramètres et définit chacune de ces propriétés pour les champs individuels.  
  
 Si l'utilisateur choisit le mode interactif, cette méthode est appelée deux fois : une fois pour définir le format de colonne en fonction des valeurs par défaut (qui varient selon le type de la colonne serveur), et une fois pour définir le format en fonction du type de colonne du choix du client choisi lors du mode interactif pour chaque colonne.  
  
 Dans les modes non interactifs, elle est appelée uniquement une fois par colonne pour attribuer le type natif ou caractère à chaque colonne, et pour définir les marques de fin de colonne et de ligne.  
  
 La méthode **BCPColFmt** vous permet de spécifier le format de fichier utilisateur pour les copies en bloc. Pour la copie en bloc, un format se compose des éléments suivants :  
  
-   un mappage des champs de fichier utilisateur aux colonnes de base de données ;  
  
-   le type de données de chaque champ de fichier utilisateur ;  
  
-   la longueur de l'indicateur facultatif pour chaque champ ;  
  
-   la longueur maximale des données par champ de fichier utilisateur ;  
  
-   la séquence d'octets de fin facultative pour chaque champ ;  
  
-   Longueur de la séquence d'octets de fin facultative  
  
 Chaque appel à **BCPColFmt** spécifie le format pour un champ de fichier utilisateur. Par exemple, pour modifier les paramètres par défaut pour trois champs dans un fichier de données utilisateur de cinq champs, appelez tout d'abord `BCPColumns(5)`, puis **BCPColFmt** cinq fois, trois de ces appels définissant votre format personnalisé. Pour les deux appels restants, attribuez BCP_TYPE_DEFAULT à *eUserDataType* et, respectivement, 0, BCP_VARIABLE_LENGTH et 0 à *cbIndicator*, *cbUserData*et *cbUserDataTerm* . Cette procédure copie les cinq colonnes, trois avec votre format personnalisé et deux avec le format par défaut.  
  
> [!NOTE]  
>  La méthode [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) doit être appelée avant tout appel à **BCPColFmt**. Vous devez appeler **BCPColFmt** une fois pour chaque colonne dans le fichier utilisateur. Le fait d'appeler **BCPColFmt** plus d'une fois pour toute colonne de fichier utilisateur génère une erreur.  
  
 Vous n'êtes pas obligé de copier toutes les données dans un fichier utilisateur vers une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour ignorer une colonne, spécifiez le format des données pour la colonne en attribuant la valeur 0 au paramètre idxServerCol. Pour ignorer un champ, vous avez encore besoin de toutes les informations pour que la méthode fonctionne correctement.  
  
 **Remarque** La fonction [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) peut être utilisée pour assurer la persistance de la spécification de format fournie par le biais de **BCPColFmt**.  
  
## <a name="arguments"></a>Arguments  
 *idxUserDataCol*[in]  
 Index de champ dans le fichier de données de l'utilisateur.  
  
 *eUserDataType*[in]  
 Type de données de champ dans le fichier de données de l'utilisateur. Les types de données disponibles sont répertoriés dans le fichier d'en-tête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (sqlncli.h) au format BCP_TYPE_XXX ; par exemple, BCP_TYPE_SQLINT4. Si la valeur BCP_TYPE_DEFAULT est spécifiée, le fournisseur essaie d'utiliser le même type que la table ou la colonne de vue. Pour les opérations de copie en bloc de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et dans un fichier lorsque le `eUserDataType` argument est BCP_TYPE_SQLDECIMAL ou BCP_TYPE_SQLNUMERIC :  
  
-   Si la colonne source n'est pas décimale ou numérique, la précision et l'échelle par défaut sont utilisées.  
  
-   Si la colonne source est décimale ou numérique, la précision et l'échelle de la colonne source sont utilisées.  
  
 *cbIndicator*[in]  
 Longueur de préfixe pour le champ. La valeur par défaut est BCP_PREFIX_DEFAULT. Les longueurs valides pour le préfixe sont 0, 1, 2, 4 et 8. La taille de préfixe 8 est la plus souvent utilisée pour indiquer que le champ est segmenté. Elle permet d'effectuer des copies en bloc efficaces de colonnes de type valeur volumineuses.  
  
 *cbUserData*[in]  
 Longueur maximale, en octets, des données de ce champ dans le fichier utilisateur, sans compter la longueur de tout indicateur de longueur ou marque de fin.  
  
 Paramètre `cbUserData` à BCP_LENGTH_NULL indique que toutes les valeurs dans les données des champs de fichier sont ou doivent être NULL. Paramètre `cbUserData` à BCP_LENGTH_VARIABLE indique que le système doit déterminer la longueur des données pour chaque champ. Pour certains champs, cela peut signifier qu'un indicateur de longueur/null est généré pour précéder les données sur une copie à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou que l'indicateur est attendu dans les données copiées vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] caractère et les types de données binaires, `cbUserData` peut être BCP_LENGTH_VARIABLE, BCP_LENGTH_NULL, 0 ou une valeur positive. Si `cbUserData` est BCP_LENGTH_VARIABLE, le système utilise l’indicateur de longueur, le cas échéant, ou d’une séquence de marque de fin pour déterminer la longueur des données. Si un indicateur de longueur et une séquence de terminaison sont fournis, la copie en bloc utilise celui qui implique le volume de données à copier le plus faible. Si `cbUserData` est BCP_LENGTH_VARIABLE, les données de type est un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type caractère ou binaire, et si un indicateur de longueur, ni une séquence de terminaison est spécifiée, le système retourne un message d’erreur.  
  
 Si `cbUserData` est égal à 0 ou une valeur positive, le système utilise `cbUserData` en tant que la longueur maximale des données. Toutefois, if, outre un positif `cbUserData`, une longueur indicateur ou marque de fin de séquence est fournie, le système détermine la longueur des données à l’aide de la méthode qui entraîne la plus petite quantité de données à copier.  
  
 Le `cbUserData` valeur représente le nombre d’octets de données. Si les données caractères sont représentées par des caractères Unicode étendus, puis un positif `cbUserData` valeur du paramètre représente le nombre de caractères multiplié par la taille, en octets, de chaque caractère.  
  
 *pbUserDataTerm*[size_is][in]  
 Séquence de marque de fin à utiliser pour le champ. Ce paramètre est utile surtout pour les types de données de caractères puisque tous les autres types sont de longueur fixe ou, dans le cas des données binaires, nécessitent un indicateur de longueur pour enregistrer avec précision le nombre d'octets présents.  
  
 Pour éviter de terminer des données extraites ou pour indiquer que les données dans un fichier utilisateur ne sont pas terminées, attribuez la valeur NULL à ce paramètre.  
  
 Si plusieurs méthodes sont employées pour définir la longueur des colonnes du fichier utilisateur (par exemple, un terminateur et un indicateur de longueur, ou un terminateur et une longueur de colonne maximale), la copie en bloc choisit celle qui implique le volume de données à copier le moins élevé.  
  
 L'interface de programmation d'applications (API) de la copie en bloc procède à la conversion des caractères Unicode vers MBCS en fonction des besoins. Prenez soin de définir comme il se doit la chaîne d'octets de terminaison et la longueur de cette même chaîne.  
  
 *cbUserDataTerm*[in]  
 Longueur, en octets, de la séquence de marque de fin à utiliser pour la colonne. Si aucune marque de fin n'est présente ou désirée dans les données, attribuez 0 à cette valeur.  
  
 *idxServerCol*[in]  
 Position ordinale de la colonne dans la table de base de données. Le premier numéro de colonne est 1. La position ordinale d'une colonne est signalée par **IColumnsInfo::GetColumnInfo** ou des méthodes semblables. Si cette valeur est 0, la copie en bloc ignore le champ dans le fichier de données.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 S_OK  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s'est produite. Pour obtenir des informations détaillées, utilisez l'interface [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) .  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, la méthode [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) n’a pas été appelée avant d’appeler cette méthode.  
  
 E_INVALIDARG  
 L'argument n'était pas valide.  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
## <a name="see-also"></a>Voir aussi  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Exécution d'opérations de copie en bloc](../native-client/features/performing-bulk-copy-operations.md)  
  
  
