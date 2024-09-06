# Thema CSS

> There's an article I'm preparing that's getting to grips with moving from ECSS to GPS, but it's not a silver bullet.
> I'm developing Thema styles as a naming convention that's "prettier" than ECSS and BEM but useful to isolate styles.

Wherever possible we should be:

- Styling RAW Html as a priority (such as forms)
- Getting our `specimen.html` file ready
- A `.gl-`obal design-system, adding only what's necessary
- A `#page` ID with repeatable `.snake-case` CSS names
    - A `#section` unique to that page (or view)

Our `.snake-case` or `#section` CSS can move up the hierarchy if it turns out we'd like to use it on another page — it can graduate to our `.gl-`obal design-system. The idea with Thema is to allow us to have flat-style CSS (not nested too deeply) yet descriptive names.

CSS shouldn't be nested more than 3 levels deep (unless short, such as `p` or `a`) and a few other rules.

1. It's nice that `.gl-Camel_Case` classes stand out a bit (easy to spot styles that are design-system)
2. Thema nicely "chops off" letters (kind of like codes) in a shorthand way to describe it's parents
3. Plain HTML should be used as much as possible over adding unecessary class names.

An example:

```css
<main id="admin">
  <nav class="gl-Nav">
    <ul>
      <li>Navigation item</li>
      <li class="gl-Nav_Icon">Navigation item with icon</li>
    </ul>
  </nav>
  <section id="dashboard">
    <div class="dash-visuals"> <!-- Scoped to `#section` name -->
      <!-- You "chop off" the first letter of it's parent -->
      <aside class="dash-v-controls"> <!-- Chop off to get `-visuals` -->
        <form class="dash-vc-settings"> <!-- .v. `-controls-` -->
          <div class="dash-vcs-wrapper"> <!-- .vc. `-settings` --> 
            <label class="dash-vcs-search"> <!-- .vcs. `-search` -->
            <div class="dash-vcs-search-box"> <!-- and so on -->
              <label>Search for data</label>
              <input type="search">
            </div>
          </div>
        </form>   <!-- /end .dash-vc-settings -->
      </aside>    <!-- /end .dash-v-controls -->
    </div>        <!-- /end .dash-visuals -->
  </section>      <!-- /end #dashboard -->
  <footer class="gl-Footer">
    ...
  </footer>
</main>
```
