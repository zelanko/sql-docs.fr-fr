---
title: IBCPSession::BCPInit (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPInit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11ddae5bacdd5428a4381ec034d9dc9f0f22b6b7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413400"
---
# <a name="ibcpsessionbcpinit-ole-db"></a>IBCPSession::BCPInit (OLE DB)
  Initialise la structure de copie en bloc, effectue une vérification des erreurs, vérifie que les données et les noms de fichiers de format sont corrects, puis les ouvre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT BCPInit(   
const wchar_t *pwszTable,  
const wchar_t *pwszDataFile,  
const wchar_t *pwszErrorFile,  
inteDirection);  
```  
  
## <a name="remarks"></a>Notes  
 Le **BCPInit** méthode doit être appelée avant toute autre méthode de copie en bloc. Le **BCPInit** méthode effectue les initialisations nécessaires pour une copie en bloc des données entre la station de travail et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le **BCPInit** méthode examine la structure de la base de données table source ou cible, pas le fichier de données. Elle spécifie des valeurs de format de données pour le fichier de données en fonction de chaque colonne dans la table de base de données, la vue ou le jeu de résultats SELECT. Cette spécification inclut le type de données de chaque colonne, la présence ou l'absence d'un indicateur de longueur ou null et des chaînes d'octet de terminateur dans les données, et la largeur des types de données de longueur fixe. Le **BCPInit** méthode définit ces valeurs comme suit :  
  
-   Le type de données spécifié est le type de données de la colonne dans la table de base de données, la vue ou le jeu de résultats SELECT. Le type de données est énuméré par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les types de données natifs spécifiés dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fichier d’en-tête Native Client (sqlncli.h). Leurs valeurs suivent le modèle BCP_TYPE_XXX. Les données sont représentées dans leur forme informatique. Autrement dit, les données d'une colonne de type de données integer sont représentées par une séquence de quatre octets de poids fort ou de poids faible selon l'ordinateur qui a créé le fichier de données.  
  
-   Si un type de données de base de données est de longueur fixe, les données du fichier de données sont également de longueur fixe. Les méthodes de copie en bloc qui traitent les données (par exemple, [IBCPSession::BCPExec](ibcpsession-bcpexec-ole-db.md)) analysent les lignes de données que la longueur des données dans le fichier de données sera identique à la longueur des données spécifiées dans la table de base de données, vue ou sélectionner la colonne liste. Par exemple, les données d'une colonne de base de données définie comme `char(13)` doivent être représentées par 13 caractères pour chaque ligne de données du fichier. Les données de longueur fixe peuvent être préfixées avec un indicateur null si la colonne de base de données autorise les valeurs NULL.  
  
-   Lors de la copie de données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le fichier de données doit avoir les données de chaque colonne de la table de base de données. Lors de la copie de données depuis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les données de toutes les colonnes de la table de base de données, de la vue ou du jeu de résultats SELECT, sont copiées vers le fichier de données.  
  
-   Lors de la copie de données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la position ordinale d'une colonne du fichier de données doit être identique à la position ordinale de la colonne de la table de base de données. Lors de la copie des données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le **BCPExec** méthode place les données selon la position ordinale de la colonne dans la table de base de données.  
  
-   Si un type de données de base de données est variable en longueur (par exemple, `varbinary(22)`) ou si une colonne de base de données peut contenir des valeurs NULL, les données du fichier de données sont préfixées par un indicateur de longueur/null. La largeur de l'indicateur varie selon le type de données et la version de la copie en bloc. Le [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) option de méthode BCP_OPTION_FILEFMT assure la compatibilité entre les fichiers de données de copie en bloc antérieurs et les serveurs exécutant les versions ultérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en indiquant à quel moment la largeur des indicateurs dans le les données sont plus étroites que prévu.  
  
> [!NOTE]  
>  Pour modifier les valeurs de format de données spécifiés pour un fichier de données, utilisez le [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) et [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) méthodes.  
  
 Copies en bloc vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être optimisé pour les tables qui ne contiennent pas d’index en définissant l’option de base de données **select dans / bulkcopy**.  
  
## <a name="arguments"></a>Arguments  
 *pwszTable*[in]  
 Le nom de la table de base de données doit être copié vers ou depuis. Le nom peut inclure le nom de la base de données ou le nom du propriétaire. Par exemple, « pubs.username.titles », « pubs..titles », « username.titles ».  
  
 Si l'argument eDirection a la valeur BCP_DIRECTION_OUT, l'argument pwszTable peut être le nom d'une vue de base de données.  
  
 Si l’argument eDirection a la valeur BCP_DIRECTION_OUT et une instruction SELECT est spécifiée à l’aide de la **BCPControl** méthode avant le **BCPExec** méthode est appelée, le *pwszTable*argument doit être défini sur NULL.  
  
 *pwszDataFile*[in]  
 Le nom du fichier doit être copié dans ou hors d’utilisateur.  
  
 *pwszErrorFile*[in]  
 Nom du fichier d'erreurs à remplir avec les messages de progression, les messages d'erreur et les copies des lignes qui n'ont pas pu être copiées d'un fichier utilisateur vers une table. Si le *pwszErrorFile* argument a la valeur NULL, aucun fichier d’erreurs n’est utilisé.  
  
 *eDirection*[in]  
 Direction de l'opération de copie, BCP_DIRECTION_IN ou _OUT BCP_DIRECTION. BCP_DIRECTION_IN indique une copie d'un fichier utilisateur vers une table de base de données ; BCP_DIRECTION_OUT indique une copie d'une table de base de données vers un fichier utilisateur.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 S_OK  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s’est produite » pour plus d’informations, utilisez le [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
 E_INVALIDARG  
 Au moins un des arguments n'a pas été spécifié correctement. Par exemple, un nom de fichier non valide a été donné.  
  
## <a name="see-also"></a>Voir aussi  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Exécution d'opérations de copie en bloc](../native-client/features/performing-bulk-copy-operations.md)  
  
  
