---
title: À l’aide d’Azure Active Directory avec le pilote ODBC | Documentation de Microsoft pour SQL Server
ms.custom: ''
ms.date: 03/21/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7486e97fb0efe9fffa9fe6eb49ee75cc6d75bfce
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634999"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>Utilisation d’Azure Active Directory avec ODBC Driver
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Fonction

Le pilote Microsoft ODBC pour SQL Server avec la version 13.1 ou version ultérieure permet les applications ODBC pour se connecter à une instance de SQL Azure à l’aide d’une identité fédérée dans Azure Active Directory avec un nom d’utilisateur/mot de passe, un jeton d’accès Azure Active Directory ou Windows Authentification intégrée (_uniquement les pilotes Windows_). Pour le pilote ODBC version 13.1, l’accès Azure Active Directory est l’authentification par jeton _Windows uniquement_. La version 17 du pilote ODBC et au-dessus de la prise en charge de cette authentification sur toutes les plateformes (Windows, Linux et Mac). Une nouvelle authentification interactive Azure Active Directory avec l’ID de connexion est introduite dans le pilote ODBC version 17.1 pour Windows. Tous ces éléments sont réalisées grâce à l’utilisation de la nouvelle source de données et les mots clés de chaîne de connexion et les attributs de connexion.

> [!NOTE]
> Le pilote ODBC sur Linux et macOS ne prend pas en charge Active Directory Federation Services. Si vous utilisez l’authentification du nom d’utilisateur/mot de passe Azure Active Directory à partir de Linux ou macOS client et votre configuration Active Directory comprend les Services fédérés, l’authentification peut échouer.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>DSN nouveaux et/ou modifié et les mots clés de chaîne de connexion

Le `Authentication` mot clé peut être utilisé lors de la connexion avec une source de données ou chaîne de connexion pour contrôler le mode d’authentification. La valeur définie dans la chaîne de connexion qui remplace dans la source de données, s’il est fourni. Le _valeur d’attribut préalable_ de le `Authentication` paramètre est la valeur calculée à partir de la chaîne de connexion et les valeurs de la source de données.

|Nom   |Valeurs|Valeur par défaut|Description|
|-|-|-|-|
|`Authentication`|(non défini), (chaîne vide), `SqlPassword`, `ActiveDirectoryPassword`, `ActiveDirectoryIntegrated`, `ActiveDirectoryInteractive`|(non défini)|Contrôle le mode d’authentification.<table><tr><th>Valeur<th>Description<tr><td>(non défini)<td>Mode d’authentification déterminé par les autres mots clés (options de connexion hérité existant).<tr><td>(chaîne vide)<td>La chaîne de connexion est « {0} » Remplacer et annuler la définition une `Authentication` valeur ensemble dans la source de données.<tr><td>`SqlPassword`<td>S’authentifier directement à une instance de SQL Server à l’aide d’un nom d’utilisateur et le mot de passe.<tr><td>`ActiveDirectoryPassword`<td>S’authentifier avec une identité Azure Active Directory à l’aide d’un nom d’utilisateur et le mot de passe.<tr><td>`ActiveDirectoryIntegrated`<td>_Pilote Windows uniquement_. S’authentifier avec une identité Azure Active Directory à l’aide de l’authentification intégrée.<tr><td>`ActiveDirectoryInteractive`<td>_Pilote Windows uniquement_. S’authentifier avec une identité Azure Active Directory à l’aide de l’authentification interactive.</table>|
|`Encrypt`|(non défini), `Yes`, `No`|(voir description)|Contrôle le chiffrement pour une connexion. Si la valeur d’attribut avant le `Authentication` paramètre n’est pas _aucun_, la valeur par défaut est `Yes`. Sinon, la valeur par défaut est `No`. La valeur d’attribut préalable de chiffrement est `Yes` si la valeur est définie sur `Yes` dans la chaîne de la source de données ou de la connexion.|

## <a name="new-andor-modified-connection-attributes"></a>Attributs de connexion nouveaux et/ou modifiés

Les éléments suivants de préconnexion connexion attributs ont été introduites ou modifiées pour prendre en charge l’authentification Azure Active Directory. Lorsqu’un attribut de connexion est une chaîne de connexion correspondante ou le mot clé DSN et est défini, l’attribut de connexion est prioritaire.

|Attribute|Type|Valeurs|Valeur par défaut|Description|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_AD_INTERACTIVE`, `SQL_AU_RESET`|(non défini)|Consultez la description de `Authentication` mot clé ci-dessus. `SQL_AU_NONE` est fourni afin de substituer explicitement un ensemble `Authentication` valeur dans la chaîne DSN et/ou de la connexion, tandis que `SQL_AU_RESET` unsets l’attribut si elle a été définie, ce qui permet de la valeur de chaîne de connexion ou de la source de données avoir la priorité.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|Pointeur vers `ACCESSTOKEN` ou NULL|NULL|Si non null, spécifie le jeton d’accès Azure AD à utiliser. C’est une erreur pour spécifier un jeton d’accès et également `UID`, `PWD`, `Trusted_Connection`, ou `Authentication` mots clés de chaîne de connexion ou leurs attributs équivalentes. <br> **Remarque :** le pilote ODBC version 13.1 prend uniquement en charge cela sur _Windows_.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(voir description)|Contrôle le chiffrement pour une connexion. `SQL_EN_OFF` et `SQL_EN_ON` désactiver et activer le chiffrement, respectivement. Si la valeur d’attribut avant le `Authentication` paramètre n’est pas _aucun_ ou `SQL_COPT_SS_ACCESS_TOKEN` est défini, et `Encrypt` non spécifiée dans la chaîne de la source de données ou de la connexion, la valeur par défaut est `SQL_EN_ON`. Sinon, la valeur par défaut est `SQL_EN_OFF`. La valeur effective de cet attribut contrôle [indique si le chiffrement sera utilisé pour la connexion.](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation)|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Non pris en charge avec Azure Active Directory, dans la mesure où les modifications de mot de passe pour les entités de sécurité AAD ne peut pas être effectuées via une connexion ODBC. <br><br>L’expiration du mot de passe pour l’authentification SQL Server a été introduite dans SQL Server 2005. Le `SQL_COPT_SS_OLDPWD` attribut a été ajouté pour permettre au client fournir l’ancien et le nouveau mot de passe pour la connexion. Lorsque cette propriété est définie, le fournisseur n'utilisera pas le pool de connexions pour la première connexion ou pour les connexions suivantes, puisque la chaîne de connexion contiendra l'« ancien mot de passe » qui a maintenant changé.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_Déconseillé_; utiliser `SQL_COPT_SS_AUTHENTICATION` la valeur `SQL_AU_AD_INTEGRATED` à la place. <br><br>Force utiliser d’authentification Windows (Kerberos sur Linux et macOS) pour la validation de l’accès sur la connexion du serveur. Lorsque l’authentification Windows est utilisée, le pilote ignore les valeurs d’identificateur et le mot de passe utilisateur fournis dans le cadre de `SQLConnect`, `SQLDriverConnect`, ou `SQLBrowseConnect` de traitement.|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Compléments d’interface utilisateur pour Azure Active Directory (pilote Windows uniquement)

La configuration du DSN et les interfaces utilisateur de connexion du pilote ont été améliorés avec les options supplémentaires nécessaires pour utiliser l’authentification auprès d’Azure AD.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Création et modification de sources de données dans l’interface utilisateur

Il est possible d’utiliser le nouveau répertoire Azure AD les options d’authentification lors de la création ou modification d’une source de données existante à l’aide de l’interface utilisateur d’installation du pilote :

`Authentication=ActiveDirectoryIntegrated` pour l’authentification intégrée à Active Directory de Azure pour SQL Azure

![CreateNewDSN_ADIntegrated.png](windows/CreateNewDSN_ADIntegrated.png)

`Authentication=ActiveDirectoryPassword` pour l’authentification du nom d’utilisateur/mot de passe Azure Active Directory pour SQL Azure

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` pour l’authentification interactive Azure Active Directory à SQL Azure

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

`Authentication=SqlPassword` pour l’authentification du nom d’utilisateur/mot de passe pour SQL Server (Azure ou autre)

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

`Trusted_Connection=Yes` pour Windows SSPI hérité intégré d’authentification

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

Les cinq options correspondent aux `Trusted_Connection=Yes` (Windows hérité existant SSPI uniquement l’authentification intégrée) et `Authentication=` `ActiveDirectoryIntegrated`, `SqlPassword`, `ActiveDirectoryPassword`, et `ActiveDirectoryInteractive`, respectivement.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>Invite de SQLDriverConnect (pilote Windows uniquement)

La boîte de dialogue invite affichée par SQLDriverConnect lorsqu’elle demande des informations requises pour établir la connexion contient trois nouvelles options pour l’authentification Azure AD :

![ServerLogin.png](windows/ServerLogin.png)

Ces options correspondent aux cinq mêmes disponibles dans la configuration du DSN UI ci-dessus.

### <a name="example-connection-strings"></a>Exemples de chaîne de connexion
1. Authentification SQL Server – syntaxe héritée. Certificat de serveur n’est pas validé, et le chiffrement est utilisé uniquement si le serveur applique il. Le nom d’utilisateur/mot de passe est transmis dans la chaîne de connexion.
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. Authentification SQL – nouvelle syntaxe. Le client demande le chiffrement (la valeur par défaut `Encrypt` est `true`) et le certificat de serveur obtient validé, quel que soit le paramètre de chiffrement (à moins que `TrustServerCertificate` est défini sur `true`). Le nom d’utilisateur/mot de passe est transmis dans la chaîne de connexion.
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. Authentification Windows (Kerberos sur Linux et macOS) intégrée à l’aide de SSPI (pour SQL Server ou SQL IaaS) – syntaxe actuelle. Certificat de serveur n’est pas validé, sauf si le chiffrement est utilisé. 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Uniquement les pilotes Windows_.) L’authentification Windows intégrée à l’aide de SSPI (si la base de données cible est dans SQL Server ou SQL IaaS) – nouvelle syntaxe. Le client demande le chiffrement (la valeur par défaut `Encrypt` est `true`) et le certificat de serveur obtient validé, quel que soit le paramètre de chiffrement (à moins que `TrustServerCertificate` est défini sur `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. Nom d’utilisateur/mot de passe l’authentification AAD (si la base de données cible est dans la base de données SQL Azure). Certificat de serveur est validé, quel que soit le paramètre de chiffrement (à moins que `TrustServerCertificate` est défini sur `true`). Le nom d’utilisateur/mot de passe est transmis dans la chaîne de connexion. 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Uniquement les pilotes Windows_.) Authentification Windows intégrée à l’aide de la bibliothèque ADAL, ce qui implique l’échange d’informations d’identification du compte Windows pour un jeton d’accès émis par AAD, en supposant que la base de données cible est dans la base de données SQL Azure. Certificat de serveur est validé, quel que soit le paramètre de chiffrement (à moins que `TrustServerCertificate` est défini sur `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Uniquement les pilotes Windows_.) L’authentification Interactive AAD utilise la technologie de l’authentification multifacteur Azure pour configurer la connexion. Dans ce mode, en fournissant l’ID de connexion, une boîte de dialogue d’authentification de Windows Azure est déclenchée et permet à l’utilisateur à entrer le mot de passe pour terminer la connexion. Le nom d’utilisateur est passé dans la chaîne de connexion.
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![WindowsAzureAuth.png](windows/WindowsAzureAuth.png)

> [!NOTE] 
>- Lorsque vous utilisez les nouvelles options d’Active Directory avec le pilote ODBC de Windows, vérifiez que le [Active Directory Authentication Library pour SQL Server](http://go.microsoft.com/fwlink/?LinkID=513072) a été installé. Lorsque vous utilisez les pilotes Linux et macOS, vérifiez que `libcurl` a été installé. Pour la version du pilote 17.2 et ultérieure, cela n’est pas une dépendance explicite dans la mesure où il n’est pas obligatoire pour les autres méthodes d’authentification ou les opérations de ODBC.
>- Pour vous connecter à l’aide d’un nom d’utilisateur du compte SQL Server et le mot de passe, vous pouvez désormais utiliser la nouvelle `SqlPassword` option, ce qui est recommandée en particulier pour SQL Azure dans la mesure où cette option active les paramètres par défaut de connexion plus sécurisées.
>- Pour vous connecter à l’aide d’un nom d’utilisateur du compte Azure Active Directory et le mot de passe, spécifiez `Authentication=ActiveDirectoryPassword` dans la chaîne de connexion et le `UID` et `PWD` mots clés avec le nom d’utilisateur et le mot de passe, respectivement.
>- Pour vous connecter à l’aide intégrée de Windows ou authentification intégrée à Active Directory (pilote Windows uniquement), spécifiez `Authentication=ActiveDirectoryIntegrated` dans la chaîne de connexion. Le pilote choisira automatiquement le mode d’authentification approprié. `UID` et `PWD` ne doit pas être spécifié.
>- Pour vous connecter à l’aide de l’authentification Active Directory Interactive (pilote Windows uniquement), `UID` doit être spécifié.

## <a name="authenticating-with-an-access-token"></a>L’authentification avec un jeton d’accès

Le `SQL_COPT_SS_ACCESS_TOKEN` attribut de préconnexion permet d’utiliser un jeton d’accès obtenu à partir d’Azure AD pour l’authentification au lieu de nom d’utilisateur et mot de passe et contourne également la négociation et l’obtention d’un jeton d’accès par le pilote. Pour utiliser un jeton d’accès, définissez le `SQL_COPT_SS_ACCESS_TOKEN` attribut de connexion à un pointeur vers un `ACCESSTOKEN` structure :

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

Le `ACCESSTOKEN` est une structure de longueur variable consistant en un 4 octets _longueur_ suivie _longueur_ octets de données opaques qui forment le jeton d’accès. En raison de la manière dont SQL Server gère les jetons d’accès, un obtenu via une [OAuth 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios) réponse JSON doit être étendu afin que chaque octet est suivi d’un octet, similaire à une chaîne de UCS-2 contenant uniquement des caractères ASCII de remplissage de 0 ; Toutefois, le jeton est une valeur opaque et la longueur spécifiée, en octets, ne doivent pas inclure toute marque de fin null. En raison de leurs contraintes de longueur et le format considérables, cette méthode d’authentification est uniquement disponible par programmation via la `SQL_COPT_SS_ACCESS_TOKEN` attribut de connexion ; aucune source de données correspondante ou le mot clé de chaîne de connexion. La chaîne de connexion ne doit pas contenir `UID`, `PWD`, `Authentication`, ou `Trusted_Connection` mots clés.

> [!NOTE]
> Le pilote ODBC version 13.1 prend uniquement en charge cette authentification sur _Windows_.

## <a name="azure-active-directory-authentication-sample-code"></a>Exemple de code d’authentification Azure Active Directory

L’exemple suivant montre le code requis pour se connecter à SQL Server à l’aide d’Azure Active Directory avec les mots clés de connexion. Notez qu’il est inutile de modifier le code de l’application ; la chaîne de connexion, ou DSN si elle est utilisée, est la seule modification nécessaire pour utiliser AAD pour l’authentification :
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
L’exemple suivant montre le code requis pour se connecter à SQL Server à l’aide d’Azure Active Directory avec authentification par jeton d’accès. Dans ce cas, il est nécessaire de modifier le code d’application pour traiter le jeton d’accès et de définir l’attribut de connexion associée.
~~~
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server}"
    SQLCHAR accessToken[] = "eyJ0eXAiOi..."; // In the format extracted from an OAuth JSON response
    ...
    DWORD dataSize = 2 * strlen(accessToken);
    ACCESSTOKEN *pAccToken = malloc(sizeof(ACCESSTOKEN) + dataSize);
    pAccToken->dataSize = dataSize;
    // Expand access token with padding bytes
    for(int i = 0, j = 0; i < dataSize; i += 2, j++) {
        pAccToken->data[i] = accessToken[j];
        pAccToken->data[i+1] = 0;
    }
    ...
    SQLSetConnectAttr(hDbc, SQL_COPT_SS_ACCESS_TOKEN, (SQLPOINTER)pAccToken, SQL_IS_POINTER);
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);      
    ...
    free(pAccToken);
~~~
Voici un exemple de chaîne de connexion pour une utilisation avec l’authentification Interactive Azure Active Directory. Notez qu’elle ne contient pas de champ PWD comme le mot de passe est entré à l’aide d’écran de l’authentification Windows Azure.
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~

## <a name="see-also"></a> Voir aussi
[Prise en charge de l’authentification basée sur le jeton de base de données SQL Azure à l’aide de l’authentification Azure AD](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

