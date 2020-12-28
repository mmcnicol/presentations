# authorization

principal:

example roles: user, admin

## declaritive authorization

these can be used at class level, or method level:
@PermitAll
@DenyAll
@RolesAllowed

these can only be used a class level:
@DeclaredRoles
@RunAs

## programmatic authorization

SessionContext
isCallerInRole()
getCallerPrincipal().getName()

SessionContext can be injected, for example:

@Resource
private SessionContext ctx;

