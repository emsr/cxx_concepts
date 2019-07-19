
Finish concepts in the main <concepts> header.  I think there are new traits that would help with strictweakordering whatever.
Here:
template <class T, class U>
  concept __WeaklyEqualityComparableWith = // exposition only
  requires(const remove_reference_t<T>& t, const remove_reference_t<U>& u)
  {
    t == u; requires Boolean<decltype(t == u)>;
    t != u; requires Boolean<decltype(t != u)>;
    u == t; requires Boolean<decltype(u == t)>;
    u != t; requires Boolean<decltype(u != t)>;
  };

snake_case everything according to .

There seem to be other concepts scattered through other headers.
<random>
//29.6.1.1
  concept UniformRandomBitGenerator
  template<classG> concept UniformRandomNumberBitGenerator
  = Invocable<G&> && UnsignedIntegral<invoke_result_t<G&>>
    && requires
 {
    G::min(); requires Same<decltype(G::min()),invoke_result_t<G&>>;
    G::max(); requires Same<decltype(G::max()),invoke_result_t<G&>>;
 };
