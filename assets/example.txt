import hashlib, hmac, os, binascii
DEFAULT_ALGO='sha256'; SUPPORTED=['sha256','sha1','sha512','blake2b']
def _get_hasher(a): return hashlib.new(a)
def hash_text(t,a=DEFAULT_ALGO): h=_get_hasher(a);h.update(t.encode());return h.hexdigest()
