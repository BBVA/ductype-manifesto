Concepts to dig in
==================

* Ductype doesn't...
  * ... work in the usual local-executable space.  It works in flake-space.  All nixpkgs software (or any other flake, really) is one command away.
  * ... just assemble pipelines and run them.  It builds new flakes on demand with sequences of commands that are automatically type-checked to assure inputs and outputs are compatible.
  * ... limits you to work with plain text input/output. You can enrich any command stdin, stdout, or stderr with a type.



There will be dragons 
---------------------

 Comp1     |      Comp2
( cat ) >dhall> ( jq '.pepito' )  :: ∀(a : Type) -> { pepito: a } -> a

cat:
#  type (dhall): ∀(a : Type) -> a -> a
  encoder: # Como transformo el dhall que me viene por la izquierda para que lo entinda cat.  "blob"
  decoder: # Como transformo lo que sale de cat para que vuelva a ser dhall. "blob"

jq:
#  type (dhall): ∀(a : Type) -> { pepito: a } -> a
  encoder: dhall-to-json
  decoder: json-to-dhall



( jq '.pepito' ) | ( jq '.pepito')  :: ∀(a : Type) -> { pepito: { pepito: a } } -> a


----

$ nmap -xo ldofijosdifj 

nix run nixpkgs#nmap -- -xo ldofijosdifj 

nmap:
  type (dhall): Text -> Text
  encoder: blob
  decoder: blob
  
$ nmap --json -xo lkjdslfjsodifj



d|  --> Como un pipe pero solo admite dhall
j|  --> Como un pipe pero solo admite json
t|  --> Como un pipe pero solo admite texto

∀nixpkgs.x | let x = nixpkgs.x

let jtdx = github:CesarGallego/nixpkgs#jtdx

let wc = nixpkgs.wc  :: Text -> Text


let isPort80open = nmap --json 192.168.1.1    j|   jq ".hosts[].ip[].port"   d|  dhall "any == 80"

$ isPort80Open                             # Escribe el flake en un directorio temporal y le un `nix run`
$ isPort80Open  >docker>  ./image.tar.gz   # Escribe el flake un directorio temporal y le haces un `nix bundle docker`
$ isPort80Open  >flake>  ./myflake         # Escribe el flake en ./myflake


let wc2:
  type: Text -> Numeric
  encoder: blob
  decoder: json


anycommand :: <arg> -> <stdin> -> (<stdout>, <stderr>)


stdin : Lee dhall escupe lo que tu me digas
stdout, stderr : Leo lo que tu me digas y escupe dhall




En dhall Text : "hola mundo"
En plaintext 
