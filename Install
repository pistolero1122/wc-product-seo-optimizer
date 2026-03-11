ID );
$desc = $post->post_content;
$meta_desc = get_post_meta( $post->ID, '_yoast_wpseo_metadesc', true );
if ( empty( $meta_desc ) ) {
$meta_desc = get_post_meta( $post->ID, '_aioseo_description', true );
}
$product = false;
if ( function_exists( 'wc_get_product' ) ) {
$product = wc_get_product( $post->ID );
}
$images = array();
if ( $product ) {
$images = $product->get_gallery_image_ids();
$thumb = $product->get_image_id();
if ( $thumb ) {
array_unshift( $images, $thumb );
}
}
$score = 0;
$checks = array();
// Title length
$title_len = mb_strlen( $title );
if ( $title_len >= 50 && $title_len <= 80 ) {
$score += 20;
$checks[] = array( 'ok' => true, 'msg' => "Title length:
{$title_len} chars (good)" );
} else {
$checks[] = array( 'ok' => false, 'msg' => "Title length:
{$title_len} chars (recommended 50–80)" );
}
// Description length
$desc_len = mb_strlen( wp_strip_all_tags( $desc ) );
if ( $desc_len >= 200 ) {
$score += 20;
$checks[] = array( 'ok' => true, 'msg' => "Description
length: {$desc_len} chars (good)" );
} else {
$checks[] = array( 'ok' => false, 'msg' => "Description
length: {$desc_len} chars (recommended ≥200)" );
}
// Images count
$img_count = count( $images );
if ( $img_count >= 3 ) {
$score += 20;
$checks[] = array( 'ok' => true, 'msg' => "Images:
{$img_count} (good)" );
} else {
$checks[] = array( 'ok' => false, 'msg' => "Images:
{$img_count} (recommended ≥3)" );
}
// Meta description
$meta_len = mb_strlen( wp_strip_all_tags( $meta_desc ) );
if ( $meta_len >= 120 && $meta_len <= 160 ) {
$score += 20;
$checks[] = array( 'ok' => true, 'msg' => "Meta
description: {$meta_len} chars (good)" );
} else {
$checks[] = array( 'ok' => false, 'msg' => "Meta
description: {$meta_len} chars (recommended 120–160)" );
}
// Price present
if ( $product && $product->get_price() !== '' ) {
$score += 20;
$checks[] = array( 'ok' => true, 'msg' => "Price set: " .
wc_price( $product->get_price() ) );
} else {
$checks[] = array( 'ok' => false, 'msg' => "Price not set" );
}
// Output
$color = $score >= 80 ? '#0f9d58' : ( $score >= 50 ? '#f4b400'
: '#db4437' );
echo '<div>';
echo "<strong>Score: </strong><span>{$score}</span>/100";
echo '<ul>';
foreach ( $checks as $c ) {
$icon = $c['ok'] ? '' : '';
echo '<li>' . esc_html( $icon . ' ' . $c['msg'] ) . '</li>';
}
echo '</ul>';
echo '<p><strong>Suggestions:</strong></p><ul>';
if ( $title_len < 50 || $title_len > 80 ) {
echo '<li>Adjust title to 50–80 chars and include the main
keyword at the start.</li>';
}
if ( $desc_len < 200 ) {
echo '<li>Expand description to explain benefits &
features; use bullets for specs.</li>';
}
if ( $img_count < 3 ) {
echo '<li>Add at least 3 images showing different
angles/use cases; add alt text.</li>';
}
if ( $meta_len < 120 || $meta_len > 160 ) {
echo '<li>Write meta description of ~120–160 chars
highlighting main benefit + CTA.</li>';
}
if ( ! ( $product && $product->get_price() !== '' ) ) {
echo '<li>Set a competitive price.</li>';
}
echo '</ul>';
echo '<p>Tip:
Connect an SEO plugin (Yoast / Rank Math) for more SEO checks.</p>';
echo '</div>';
}
public function save_meta( $post_id, $post ) {
// Nothing to save for the MVP; placeholder for future use.
}
}
new WC_Listing_Optimizer_MVP();

