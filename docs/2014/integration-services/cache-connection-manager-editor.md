---
title: Éditeur de gestionnaire de connexions du cache | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cacheconnection.f1
ms.assetid: 0d8f9324-0c35-4eea-b06d-da3cc2426d2c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0b9ede014f68d06f84132664ee3f4e1413f715e0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130829"
---
# <a name="cache-connection-manager-editor"></a>Éditeur du gestionnaire de connexions du cache
  Le gestionnaire de connexions du cache lit un dataset de référence à partir de la transformation de cache ou d'un fichier cache (.caw) et peut enregistrer les données dans un fichier cache. Les données sont toujours stockées en mémoire.  
  
> [!NOTE]  
>  Le gestionnaire de connexions du cache ne prend pas en charge les types de données de l'objet BLOB (Binary Large Object) DT_TEXT, DT_NTEXT et DT_IMAGE. Si le dataset de référence contient un type de données d'objet BLOB, le composant échoue lorsque vous exécutez le package. Vous pouvez utiliser l' **Éditeur du gestionnaire de connexions du cache** pour modifier des types de données de colonne.  
  
 La transformation de recherche effectue des recherches sur le dataset de référence.  
  
 La boîte de dialogue **Éditeur du gestionnaire de connexions du cache** inclut les onglets suivants :  
  
-   [Onglet Général](#generaltab)  
  
-   [Onglet colonnes](#columnstab)  
  
 Pour en savoir plus sur le gestionnaire de connexions du cache, consultez [Cache Connection Manager](connection-manager/cache-connection-manager.md).  
  
##  <a name="generaltab"></a> Onglet Général  
 Utilisez l’onglet **Général** de la boîte de dialogue **Éditeur du gestionnaire de connexions du cache** pour indiquer s’il faut lire le cache depuis un fichier ou l’enregistrer dans un fichier.  
  
### <a name="options"></a>Options  
 **Nom du gestionnaire de connexions**  
 Fournit un nom unique pour la connexion de fichiers cache dans le flux de travail. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Description**  
 Décrit la connexion. Il est recommandé de décrire la connexion selon son objectif, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
 **Utiliser un cache de fichier**  
 Indiquez s'il faut utiliser ou non un fichier cache.  
  
> [!NOTE]  
>  Le niveau de protection du package ne s'applique pas au fichier cache. Si le fichier cache contient des informations sensibles, utilisez une liste de contrôle d'accès (ACL) pour restreindre l'accès à l'emplacement ou au dossier dans lequel vous stockez le fichier. Vous devez autoriser l'accès à certains comptes uniquement. Pour plus d’informations, consultez [Accéder aux fichiers utilisés par des packages](../../2014/integration-services/access-to-files-used-by-packages.md).  
  
 Si vous configurez le gestionnaire de connexions du cache pour utiliser un fichier cache, il effectuera l'une des actions suivantes :  
  
-   Il enregistrera les données dans le fichier lorsqu'une transformation du cache est configurée pour écrire des données depuis une source de données dans le flux de données dans le gestionnaire de connexions du cache. Pour plus d'informations, consultez [Cache Transform](data-flow/transformations/cache-transform.md).  
  
-   Il lira des données à partir du fichier cache.  
  
 **Nom de fichier**  
 Tapez le chemin d'accès et le nom du fichier cache.  
  
 **Parcourir**  
 Recherchez le fichier cache.  
  
 **Actualiser les métadonnées**  
 Supprimez les métadonnées de colonne dans le gestionnaire de connexions du cache et remplissez à nouveau celui-ci avec les métadonnées de colonne d'un fichier cache sélectionné.  
  
##  <a name="columnstab"></a> Onglet Colonnes  
 Utilisez l'onglet **Colonnes** de la boîte de dialogue **Éditeur du gestionnaire de connexions du cache** pour configurer les propriétés de chaque colonne dans le cache.  
  
### <a name="options"></a>Options  
 **Colonne**  
 Spécifiez le nom de la colonne.  
  
 **Position d'index**  
 Spécifiez quelles colonnes sont des colonnes d'index en indiquant la position d'index de chaque colonne. L'index est une collection composée d'une ou de plusieurs colonnes.  
  
 Pour les colonnes qui ne sont pas des index, la position d'index est 0.  
  
 Pour les colonnes d'index, la position d'index est un nombre séquentiel, positif. Ce nombre indique l'ordre dans lequel la transformation de recherche compare des lignes dans le dataset de référence aux lignes de la source de données d'entrée. La colonne comportant la plupart des valeurs doit avoir la position d'index la plus faible.  
  
> [!NOTE]  
>  Lorsque la transformation de recherche est configurée pour utiliser un gestionnaire de connexions du cache, seules les colonnes d'index dans le dataset de référence peuvent être mappées avec des colonnes d'entrée. En outre, toutes les colonnes d'index doivent être mappées.  
  
 **Type**  
 Spécifiez le type de données de la colonne.  
  
 `Length`  
 Indique le type de données de la colonne. Si le type de données, vous pouvez mettre à jour `Length`.  
  
 `Precision`  
 Spécifie la précision pour certains types de données de colonne. La précision est le nombre de chiffres qui composent un nombre. Si le type de données, vous pouvez mettre à jour `Precision`.  
  
 `Scale`  
 Spécifie l'échelle pour certains types de données de colonne. L'échelle est le nombre de chiffres à droite du séparateur décimal dans un nombre. Si le type de données, vous pouvez mettre à jour `Scale`.  
  
 `Code Page`  
 Spécifie la page de codes pour le type de colonne. Si le type de données, vous pouvez mettre à jour `Code Page`.  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de recherche](data-flow/transformations/lookup-transformation.md)  
  
  
